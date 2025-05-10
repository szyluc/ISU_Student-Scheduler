# Student-Scheduler

This is my project I presented at Illinois State University's 2025 Research Symposium. 

Using AI models from Hugging Face, the user can enter their responsibilities for the days of the week and receive a sample schedule they can follow in the program's output. Following the schedule generation, the user can choose to export their schedule to their personal Google Calendar, allowing for ease-of-use and access anywhere. 

-------------------------------------------------------------------------------------------------------------------------------

I used two different models, Deepseek R1 and Qwen 2.5. You can swap between the two by switching which model is commented out in the "# MODEL LOADING HERE" code block. 

The following code block is used for authenticating with the user's Google Calendar. Read and write scopes are both required in order to be able to successfully export the generated schedule. 

After Google authentication, the next code block is the "meat and potatoes" of the project, where I have the intro message for the user, along with the system prompt for the model to follow when generating it's response. I had trouble finding a system prompt that worked, but eventually I got some help from AI and it works now. 

The "generate_user_schedule" and "export_to_google_calendar" functions in this code block are called when the user hits the "Generate" and "Export" buttons on the Gradio interface. In generation, the user's input is tokenized, then sent to the model, where it generates a tokenized output based on user input which is finally decoded and returned. In the export function, regex patterns are used to parse through the output to determine which parts need to be sent out for each day's tasks in the user's calendar. They are categorized by "summary", "start time", and "end time". 

The last section is for building the Gradio interface that the user interacts with. This is a very basic interface that provides the user with a text box where they enter their information, and then an output box that gives them their generated schedule. The user then has the option to export by clicking the button. 
