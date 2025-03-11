# Video Analysis with GPT-4o

The aim of this repository is to demonstrate the capabilities of GPT-4o to analyze and extract insights from a video file or a video URL (e.g., YouTube).

## Table of Contents

- [Video Analysis with GPT-4o](#video-analysis-with-gpt-4o)
  - [Table of Contents](#table-of-contents)
  - [Prerequisites](#prerequisites)
    - [Set up a Python virtual environment in Visual Studio Code](#set-up-a-python-virtual-environment-in-visual-studio-code)
    - [Environment Configuration](#environment-configuration)
  - [Video Analysis Script](#video-analysis-script)
    - [Usage](#usage)
    - [Parameters](#parameters)
    - [Example](#example)
  - [Video Shot Analysis Script](#video-shot-analysis-script)
    - [Usage](#usage-1)
    - [Parameters](#parameters-1)
    - [Example](#example-1)
  - [YouTube Video Downloader Script](#youtube-video-downloader-script)
    - [Usage](#usage-2)
    - [Parameters](#parameters-2)
    - [Example](#example-2)

## Prerequisites
+ An OpenAI key

I used Python 3.12.5, [Visual Studio Code with the Python extension](https://code.visualstudio.com/docs/python/python-tutorial), and the [Jupyter extension](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.jupyter) to test this example.

### Set up a Python virtual environment in Visual Studio Code

1. Open the Command Palette (Ctrl+Shift+P).
1. Search for **Python: Create Environment**.
1. Select **Venv**.
1. Select a Python interpreter. Choose 3.10 or later.

It can take a minute to set up. If you run into problems, see [Python environments in VS Code](https://code.visualstudio.com/docs/python/environments).

### Environment Configuration

Create a `.env` file in the root directory of your project with the following content. You can use the provided [`.env-sample.ini`](.env-sample.ini) as a template:

```
SYSTEM_PROMPT="You are an expert on Video Analysis. You will be shown a series of images from a video. Describe what is happening in the video, including the objects, actions, and any other relevant details. Be as specific and detailed as possible."

OPENAI_API_KEY=
```

The needed libraries are specified in [requirements.txt](requirements.txt).

## Video Analysis Script

The `video-analysis-with-gpt-4o.py` script demonstrates the capabilities of GPT-4o to analyze and extract insights from a video file or a video URL (e.g., YouTube). This script is useful for analyzing videos in detail by splitting them into smaller segments and extracting frames at a specified rate. This allows for a more granular analysis of the video content, making it easier to identify specific events, actions, or objects within the video. This script is particularly useful for:

- Detailed video analysis for research or academic purposes.
- Analyzing training or instructional videos to extract key moments.
- Reviewing security footage to identify specific incidents.

Here is the code of this demo: [video-analysis-with-gpt-4o.py](video-analysis-with-gpt-4o.py)

### Usage

To run the `video-analysis-with-gpt-4o.py` script, execute the following command:
```
streamlit run video-analysis-with-gpt-4o.py
```

### Parameters

- **Video source**: Select whether the video is from a file or a URL.
- **Continuous transmission**: Check this if the video is a continuous transmission.
- **Transcribe audio**: Check this to transcribe the audio using Whisper.
- **Show audio transcription**: Check this to display the audio transcription.
- **Number of seconds to split the video**: Specify the interval for each video segment.
- **Number of seconds per frame**: Specify the number of seconds between each frame extraction.
- **Frames resizing ratio**: Specify the resizing ratio for the frames.
- **Save the frames**: Check this to save the extracted frames to the "frames" folder.
- **Temperature for the model**: Specify the temperature for the GPT-4o model.
- **System Prompt**: Enter the system prompt for the GPT-4o model.
- **User Prompt**: Enter the user prompt for the GPT-4o model.

### Example

To analyze a YouTube video with a segment interval of 60 seconds, extracting 1 frame every 30 seconds, you would set the parameters as follows:

- **Video source**: URL
- **URL**: `https://www.youtube.com/watch?v=example`
- **Number of seconds to split the video**: 60
- **Number of seconds per frame**: 30

Then click the "Analyze video" button to start the analysis.

A screenshot:

<img src="./Screenshot.png" alt="Sample Screenshot"/>

To deploy the application on your Azure tenant in an Azure Container Registry (Docker), follow this [guide: Build and store an image by using Azure Container Registry](https://learn.microsoft.com/en-us/training/modules/deploy-run-container-app-service/3-exercise-build-images) and then create and deploy the web app following this [guide: Create and deploy a web app from a Docker image](https://learn.microsoft.com/en-us/training/modules/deploy-run-container-app-service/5-exercise-deploy-web-app).

## Video Shot Analysis Script

The `video_shot_analysis.py` script will download the specified video, split it into shots based on the defined interval, extract frames at the specified rate, perform the analysis on each shot, and save the analysis results to JSON files in the analysis subdirectory within the main video analysis directory. If `max_duration` is set, only up to that duration of the video will be processed. This script is useful for:

- Detailed video analysis for research or academic purposes.
- Analyzing training or instructional videos to extract key moments.
- Reviewing security footage to identify specific incidents.

Here is the code of this demo: [video_shot_analysis.py](video_shot_analysis.py)

### Usage

To run the `video_shot_analysis.py` script, execute the following command:
```
streamlit run video_shot_analysis.py
```

### Parameters

- **Video source**: Select whether the video is from a file or a URL.
- **Continuous transmission**: Check this if the video is a continuous transmission.
- **Transcribe audio**: Check this to transcribe the audio using Whisper.
- **Show audio transcription**: Check this to display the audio transcription.
- **Shot interval in seconds**: Specify the interval for each video shot.
- **Frames per second**: Specify the number of frames to extract per second.
- **Frames resizing ratio**: Specify the resizing ratio for the frames.
- **Save the frames**: Check this to save the extracted frames to the "frames" folder.
- **Temperature for the model**: Specify the temperature for the GPT-4o model.
- **System Prompt**: Enter the system prompt for the GPT-4o model.
- **User Prompt**: Enter the user prompt for the GPT-4o model.
- **Maximum duration to process (seconds)**: Specify the maximum duration of the video to process. If the video is longer, only this duration will be processed. Set to 0 to process the entire video.

### Example

To analyze a YouTube video with a shot interval of 60 seconds, extracting 1 frame per second, and processing only the first 120 seconds of the video, you would set the parameters as follows:

- **Video source**: URL
- **URL**: `https://www.youtube.com/watch?v=example`
- **Shot interval in seconds**: 60
- **Frames per second**: 1
- **Maximum duration to process (seconds)**: 120

Then click the "Analyze video" button to start the analysis.

## YouTube Video Downloader Script

The `yt_video_downloader.py` script allows you to download a segment of a YouTube video, convert it to MP4 format, and ensure the file size is under 200 MB. This script is useful for:

- Downloading and saving specific parts of a YouTube video for offline viewing.
- Extracting segments of a video for use in presentations or reports.
- Ensuring the downloaded video segment is of a manageable size for sharing or storage.

Here is the code of this demo: [yt_video_downloader.py](yt_video_downloader.py)

### Usage

To run the `yt_video_downloader.py` script, execute the following command:
```
python yt_video_downloader.py
```

### Parameters

- **YouTube URL**: Enter the URL of the YouTube video.
- **Start time in seconds**: Specify the start time of the segment to download (default is 0).
- **End time in seconds**: Specify the end time of the segment to download (default is 60).
- **Output directory**: Specify the directory to save the downloaded segment (default is 'output').

### Example

To download a 60-second segment of a YouTube video starting at 30 seconds, you would set the parameters as follows:

- **YouTube URL**: `https://www.youtube.com/watch?v=example`
- **Start time in seconds**: 30
- **End time in seconds**: 90
- **Output directory**: `output`

Then run the script to download and convert the segment:
```
python yt_video_downloader.py
```

The script will save the segment as an MP4 file in the specified output directory and ensure the file size is under 200 MB.
