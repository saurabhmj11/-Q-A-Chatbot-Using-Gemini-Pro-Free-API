# -Q-A-Chatbot-Using-Gemini-Pro-Free-API
#GeminiPro #AI #NaturalLanguageProcessing #ConversationalAI #Streamlit #GoogleGenerativeAI #TechInnovation #OpenSource
Step 1: Set up your Project Environment
1.1. Create a new project directory and navigate to it using your terminal or command prompt.

bash
Copy code
mkdir gemini-llm
cd gemini-llm
Step 2: Create Virtual Environment
2.1. Create a virtual environment to manage dependencies.

bash
Copy code
python -m venv venv
2.2. Activate the virtual environment.

On Windows:
bash
Copy code
venv\Scripts\activate
On Unix or MacOS:
bash
Copy code
source venv/bin/activate
Step 3: Install Dependencies
3.1. Install required packages using pip.

bash
Copy code
pip install streamlit python-dotenv google-generativeai
Step 4: Set up Google API Key
4.1. Create a .env file in your project directory and add your Google API key.

dotenv
Copy code
# .env
GOOGLE_API_KEY=your_google_api_key
Step 5: Create Python Script
5.1. Create a Python script (e.g., app.py) in your project directory.

python
Copy code
# app.py
from dotenv import load_dotenv
load_dotenv()  # Load environment variables

import streamlit as st
import os
import google.generativeai as genai

genai.configure(api_key=os.getenv("GOOGLE_API_KEY"))

model = genai.GenerativeModel("gemini-pro") 
chat = model.start_chat(history=[])

def get_gemini_response(question):
    response = chat.send_message(question, stream=True)
    return response

# Initialize session state for chat history if it doesn't exist
if 'chat_history' not in st.session_state:
    st.session_state['chat_history'] = []

st.set_page_config(page_title="Q&A Demo")
st.header("Gemini LLM Application")

input_text = st.text_input("Input: ", key="input")
submit = st.button("Ask the question")

if submit and input_text:
    response = get_gemini_response(input_text)
    st.session_state['chat_history'].append(("You", input_text))
    st.subheader("The Response is")
    for chunk in response:
        st.write(chunk.text)
        st.session_state['chat_history'].append(("Bot", chunk.text))

st.subheader("The Chat History is")
for role, text in st.session_state['chat_history']:
    st.write(f"{role}: {text}")
Step 6: Run the Application
6.1. Run the Streamlit application.

bash
Copy code
streamlit run app.py
6.2. Visit the provided URL in your browser to interact with the Gemini LLM Application.

Step 7: Share on GitHub
7.1. Create a GitHub repository for your project.

7.2. Push your code to the repository.

bash
Copy code
git init
git add .
git commit -m "Initial commit"
git remote add origin your_repository_url
git push -u origin master
Replace your_google_api_key in the .env file with your actual Google API key and your_repository_url with the URL of your GitHub repository.

Now you have a Q&A application powered by the Gemini Pro model, and it's ready to be shared on LinkedIn and GitHub! Feel free to customize the code, enhance the features, and iterate on the project.






