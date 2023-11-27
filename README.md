# Hypothetical Document Embeddings (HyDE) for Unsupervised Dense Retrieval


**HyDE** zero-shot instructs GPT3 to generate a fictional document and re-encodes it with unsupervised retriever Contriever to search in its embedding space.
HyDE significantly outperforms Contriever across tasks and languages and it does not require any human labeled relevance judgement.

![hyde pipeline](https://github.com/vishalgoudmogili/cs421-research-study/assets/144625177/24ba2ed4-90bf-44a6-b41f-6ddcb6254610)


## Steps to run the code

1. Install `pyserini` by following the [guide](https://github.com/castorini/pyserini#-installation). We use pyserini to conduct dense retrieval and evaluation. Also run the `setup.py` to install the necessary packages.


2. Download the prebuilt Contrever faiss index
```
wget  https://www.dropbox.com/s/dytqaqngaupp884/contriever_msmarco_index.tar.gz
tar -xvf contriever_msmarco_index.tar.gz
```

or 

you can directly download it from https://www.dropbox.com/s/dytqaqngaupp884/contriever_msmarco_index.tar.gz extract it and then keep in the folder where you're working

3. Setup GPT3 API key

   - Go to link: https://platform.openai.com/docs/overview and you should be able to see the openai platform like below:
     
     <img width="1503" alt="docs home" src="https://github.com/vishalgoudmogili/cs421-research-study/assets/144625177/5083c124-2b75-4b14-8947-629b9b63d65d">
     
   - Then expand the side panel by a click and then select API keys as shown below:
     
     <img width="1506" alt="select api keys" src="https://github.com/vishalgoudmogili/cs421-research-study/assets/144625177/8f19094d-ba84-4fa3-8132-3bed9c4015b2">
     
   - Now click on button "Create new secret key" and enter any secret key and click on create secret key. This will create you secret key:
     
     <img width="1507" alt="create new secret key" src="https://github.com/vishalgoudmogili/cs421-research-study/assets/144625177/120c4443-4686-4f88-9ad4-38f1cb906ab5">
     <img width="1507" alt="enter secret key" src="https://github.com/vishalgoudmogili/cs421-research-study/assets/144625177/f87580b6-3450-47bf-a171-d069fe5338df">
     
   - A confirmation toaster will appear saying API key generated you can copy it and click on done:
     
     <img width="1508" alt="confirmation" src="https://github.com/vishalgoudmogili/cs421-research-study/assets/144625177/00a16dc0-ca24-4b27-93de-a11f37d3d797">
     <img width="1508" alt="copy and done" src="https://github.com/vishalgoudmogili/cs421-research-study/assets/144625177/7ea8d631-b4e3-4c53-9cdd-0b08a9079eea">

   After copying the API key please follow the below instructions as per machine type:
#### If you're using MacOS then setup the API Key using the below instructions: 

  - Open Terminal: You can find it in the Applications folder or search for it using Spotlight (Command + Space).

  - Edit Bash Profile: Use the command nano ~/.bash_profile or nano ~/.zshrc (for newer MacOS versions) to open the profile file in a text editor.

  - Add Environment Variable: In the editor, add the line below, replacing your-api-key-here with your actual API key:

    ```
    export OPENAI_API_KEY='your-api-key-here'
    ```
  - Save and Exit: Press Ctrl+O to write the changes, followed by Ctrl+X to close the editor.

  - Load Your Profile: Use the command source ~/.bash_profile or source ~/.zshrc to load the updated profile.

  - Verification: Verify the setup by typing echo $OPENAI_API_KEY in the terminal. It should display your API key.

#### If you're using Windows then setup the API Key using the below instructions: 

  - Open Command Prompt: You can find it by searching "cmd" in the start menu.

  - Set environment variable in the current session: To set the environment variable in the current session, use the command below, replacing your-api-key-here with your actual API key:

    ```
    setx OPENAI_API_KEY "your-api-key-here"
    ```
  - This command will set the OPENAI_API_KEY environment variable for the current session.

  - Permanent setup: To make the setup permanent, add the variable through the system properties as follows:

    - Right-click on 'This PC' or 'My Computer' and select 'Properties'.
    - Click on 'Advanced system settings'.
    - Click the 'Environment Variables' button.
    - In the 'System variables' section, click 'New...' and enter OPENAI_API_KEY as the variable name and your API key as the variable value.
  - Verification: To verify the setup, reopen the command prompt and type the command below. It should display your API key: echo %OPENAI_API_KEY%


4. Run `hyde-dl19.ipynb`, it will run the experiment on the TREC DL19 dataset. Run `implementation-of-hyde.ipynb`, it will go through HyDE pipeline with an example query.
