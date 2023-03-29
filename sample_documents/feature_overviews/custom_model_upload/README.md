# Custom Model Upload Service

## Overview
Our company has thousands of collaborators. The diversity of our team members offers an opportunity to collaborate and develop solutions that can shape how we work. For the <b>AI System</b> team, it opened the opportunity to create the <b>Custom Model Upload</b> Service.

The <b>Custom Model Upload Service</b> enables Python developers to create and deploy any model into the AI System. In this document, you will learn how to upload and use your model in minutes, via REST API.

## Benefits
When you upload your model, you can expect the following benefits:
- Upload any model with Python programming language.
- Make your model available on the same day you publish it.
- Make your model cost-friendly.
- Publish your model to a development environment with only two single-click approval stages.
- Share your model with other collaborators.

## Requirements
Before you contribute with the AI System team, you must meet the following requirements:
- You must write your model in Python code, which runs and returns results locally.
- You must have access to the <a href="">DevOps Repository</a> to download the <a href="">Custom Model Upload</a> directory.
- You must authorize your action in the <a href="">AI System API</a> with an `API_KEY`. To get your `API_KEY`, read the <a href="">Onboarding</a> guide.

> <b>Important:</b><br>
You will upload your code to a repository that supports DVC and git Large File Support (LFS) for handling data files such as configuration files and model binaries. <b>Do not</b> upload such files without DVC or git LFS.

## Step-by-Step Guide
This section contains a step-by-step guide to upload your model. Navigate the document with the following list:
1. [Clone the `custom_model_publisher` directory and populate it](#1-clone-the-custom_model_publisher-directory-and-populate-it)
1. [Implement the `NewModel` base class interface](#2-implement-the-newmodel-base-class-interface)
1. [Upload your Model](#3-upload-your-model)
1. [Run your model with the AI System API](#4-run-your-model-with-the-ai-system-api)


## 1. Clone the `custom_model_publisher` Directory and Populate It
In this section, you will learn how to populate the `custom_model_publisher` repository with your code to be successfully deployed in the AI System.

Before you begin, ensure that your model has a unique descriptive name to use as its identifier. Then, follow the steps below:

1. Clone the <a href=""><code>custom-model-publisher</code></a> repository in your local computer.
1. Ensure that you are working in the `develop` branch of the repository.
1. Open the `src` directory and then open the `new_custom_model` folder.
1. Copy your Python model inside the `new_custom_model` folder.
1. Open the `__init__.py` file and do the following:
    1. Change the attribute in `MODEL_NAME`.
    1. Set the version number for your model.
1. Rename the `new_custom_model` folder with the value you changed in the `MODEL_NAME` attribute during the previous step.
1. Open the `setup.py` file in the `src` directory, and rename the `PKG_DIR_NAME` attribute to the name of your model.
    
> <b>Important:</b><br>
In steps 5 and 6, you change the attribute in `__init__.py/MODEL_NAME` and rename the `new_custom_model` folder. Ensure that your changes have the same name and use only lower case letters and underscores.

### Dependencies
If your model relies on dependencies, you must add your model's dependencies to the current information in the `requirements.txt` file. Follow the example below:

```sh
tensorflow=2.3.1
uvicorn=0.12.2
fastapi=0.63.0
```

> <b>Note:</b><br>
All your dependencies must be OSS-approved by the <a href="">Information Security Department</a>. 

### Data Files
If your model requires data files, do the following: 
1. Open the `setup.py` file in the repository.
1. Review the file extensions that the repository supports.
1. Create a folder called ` data` into the `src` directory with the data files for your model.
1. Ensure that your data files comply with the extensions listed in `setup.py`.

After you populate the repository with your code, you can continue to implement the base class interface to your model. 

## 2. Implement the `NewModel` Base Class Interface
In this section you will use the <a href=""><code>custom_model_framework</code></a> library, which you can download from the <a href="">DevOps Repository</a>, to implement an interface that you can later call through the AI System API.

Follow the steps below to implement the `NewModel` Base Class Interface:

1. Open the `custom_model.py` file or create a new Python file in the same location.
1. Call the functions from your model with the methods from the `custom-model-framework` library. Follow the example below:

    ``` sh
    [THIS IS INTELLECTUAL PROPERTY]
    ```
1. Ensure that you imported correctly your implementation in the `__init.py__.py` file.

You can read about the `NewModel` methods in the following table:

<figure>
  <table>
      <tr>
          <th>Method</th>
          <th>Definition</th>
          <th>Notes</th>
      </tr>
    <tr>
      <td colspan="3">This is intellectual property</td>
    </tr>
  </table>
  <figcaption><b>Table 1:</b>Methods in <code>NewModel</code></figcaption>
 </figure>

## 3. Upload your Model
In this section, you will upload your model to the AI System. This section contains two methods to upload your model:
- [Publish your Model with the `custom-model-publisher`](#publish-your-model-with-the-custom-model-publisher)
- [Publish your Model with the `submit-model` endpoint in the AI System API](#publish-your-model-with-the-submit-model-endpoint)

### Publish your Model with the `custom-model-publisher`
Since you included your model to the `di-platform-model-publisher` repository, your model can be deployed by following the steps below:
1. Create a new feature branch with your implementation in the <a href=""><code>custom-model-publisher</code></a>.
1. Upload the files to the new feature branch.
1. Push your new feature branch back into the `custom-model-publisher` repository.

> <b>Note:</b><br>
You can do the previous steps using git commands.

When you push your branch to the repository, you also trigger an automatic pipeline. The pipeline does the following:
1. Installs the requirements.
1. Runs the model.
1. Wraps the solution to a new package.
1. Tests the deployment. 

If the pipeline finds an error, you will receive an email and you can review the logs to correct and deploy your model again.

> <b>Note:</b><br>
After you successfully upload your model, any modifications <b>">must</b> be accompanied by a version change. Read the Step 5 from the [1. Clone the `custom-model-publisher` and Populate It](#1-clone-the-custom_model_publisher-directory-and-populate-it) section.

### Publish your Model with the `submit-model` endpoint
After you [Implement the `NewModel` Base Class](#2-implement-the-newmodel-base-class-interface) in your model, you can publish your code. 

This method is optimized for models that have a wheel file (`.whl`)  hosted in the DevOps repository, or a wheel file link in some storage. 

><b>Note:</b><br>
The link needs to point directly to the wheel file.

To upload your model, use the following endpoint in the <a href="">AI System API</a>:

- [POST /v2/trigger/task](#post-v2triggertask)

#### POST /v2/trigger/task
- Required parameters
    <table>
        <tr>
            <th>Parameter</th>
            <th>Type</th>
            <th>Required</th>
            <th>Description</th>
        </tr>
        <tr>
          <td colspan="4">This is intellectual property</td>
        </tr>
    </table>

- Request body example
    ```sh
    [THIS IS INTELLECTUAL PROPERTY]
    ```
- Responses
    ```sh
    200: SUCCESS
    [THIS IS INTELLECTUAL PROPERTY
    ```

After you receive the `200: SUCCESS` response, your model is available for you to call through the <a href="">AI System API</a>.

## 4. Run your Model with the AI System API
In this section, you will learn how to run your model with the AI System API. 

The endpoint to review your model is the following:
```sh
GET /results/{task_id}
```

The endpoint does not have any payload requirements, and your request triggers one of the following responses:

```sh
    200: SUCCESS
    [THIS IS INTELLECTUAL PROPERTY]
```

```sh
    202: STARTED
    [THIS IS INTELLECTUAL PROPERTY]
```

```sh
    401: FAILURE
    [THIS IS INTELLECTUAL PROPERTY]
```

After you verify your model works via API, you can promote it to UAT environment using a pre-built <a href="">Azure DevOps Pipeline</a> which requires two parameters from you: `MODEL_NAME` and `MODEL_VERSION`.  

<b>Congratulations!</b>

You have successfully uploaded a new model to the AI System. You can now share your solution with coworkers.
