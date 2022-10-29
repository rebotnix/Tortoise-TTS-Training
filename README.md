# Tortoise-TTS-Training
 Community framework for training tortoise (Expermental and first alpha version 29ht october 2022)

# About Tortoise 
The original tortoise was written by James Betker. 
This github is an opensource version for a training Tortoise uses several frameworks to generate high quality synthetic audio. 
We want to provide new results in fundamental AI research, as well as useful applications and added value. We are a community with developers from all over the world working together.

The community for this project works on a discord server. 
Link: https://discord.gg/qc5D9sqv 

# Understand the license agreement before you start using this project
The developers commit in their license not to add Deep Fakes or other living beings a harm. The project is license free, you can use it in commercial or research with the following conditions. 
The license based on MIT and extends it with the addition of the "No HARM AI". "No HARM AI" means, that generated AI content will be marked by "Content was created by Tortoise-TTS-Community" and that this content is truthful. This is an easy to understand rule and we ask you to follow it, please. We want to demonstrate the potential of AI applications can have without showing these overwhelming DeepFake applications.

# The projects we are working on.

# Indie game development
The game industry in the indie sector is great. In order to create new games, we want to support them with this project and give them the opportunity to develop multilingual games with emotional and cool voices. 

# Medical institutions 
We want to support people who have lost their voice, e.g. through illness, to get back an emotional voice. We are developing low cost hardware which allows to create a voice again with a speech computer. 

# Low Power Devices
Research porting large models to embedded hardware devices to reduce power consumption in data centers.

# # More projects to come. 
TBA

## Setup
We used Python 3.7 till 3.9.9 and [PyTorch](https://pytorch.org/) 1.10.1 to train and test our models, but the codebase is expected to be compatible with Python 3.7 or later and recent PyTorch versions. The codebase also depends on a few Python packages.

Currently we tested it on Ubuntu X86 Intel in combination with NVIDIA 4 x RTX 3090. 

## Installation 
It is recommended that you use virtualenv or conda for a virtual Python for your environment.

```bash
# on Ubuntu or Debian
sudo apt update && sudo apt install ffmpeg

# please see each folder for the requirements to use them
pip -r requirements.txt
```

# Framework
To train a Tortoise TTS model, you need to prepare your dataset first and then train several models. We want offer the whole pipeline to do it. Currently we have the preparing pipeline ready.

# 01.annotate_audio
To create a dataset manually, it is mandatory to create it automatically. Creating speech to text manually can be very time-consuming and costly. 
This framework allows to segment the audio track of any media source, e.g. *.mp4,*.ts, *.mp3, *.wav etc. It also allows to convert audio from webserver or livestreams and to automatically generate training material and also split the audio file in the time and segments. The segments are splitted in 6 seconds up to a maximum of 20 seconds. 
When you use the auto mode, it detect automaticly the language. It is recommended to divide the audio material into 2 hour blocks (more can work.)

We use the open source HQ Whisper model to generate text to speech train files. We use the whisper API for segmenting and splitten the files. You do not have to care about the API, we offer
a simple CLI interface to do it.

#Currently we support these languages for speech to text:
"english",chinese",german",spanish",russian",korean",french",japanese","portuguese",turkish",polish",catalan",dutch",arabic",swedish",italian",indonesian","hindi","finnish","vietnamese",
"hebrew","ukrainian","greek","malay","czech",romanian","danish","hungarian","tamil","norwegian","thai","urdu","croatian","bulgarian","lithuanian","latin","maori","malayalam","welsh","slovak","telugu","persian","latvian","bengali","serbian","azerbaijani","slovenian","kannada","estonian","macedonian","breton","basque","icelandic","armenian","nepali","mongolian","bosnian","kazakh","albanian",
"swahili","galician","marathi","punjabi","sinhala","khmer","shona","yoruba","somali","afrikaans","occitan","georgian","belarusian","tajik","sindhi",
"gujarati","amharic","yiddish","lao","uzbek","faroese","haitian creole","pashto","turkmen","nynorsk","maltese "sanskrit","luxembourgish","myanmar","tibetan","tagalog","malagasy","assamese","tatar","hawaiian","lingala","hausa"," bashkir","javanese","su": "sundanese",

Example CLI to generate a train.txt from an audio source:
```
python generate_train.py youraudio.mp3 --model small --train_dir DatasetTrainDir
```

Parameters:
generate_train.py   -> Script for generating Trainingsdata
--model small       -> Defines the speech to text models. Usefull values are tiny, small and medium. If the model is not in your local cache, it will downloaded automaticly. 
--train_dir         -> Defines the outputdir where the splitted mp3 chunks and final train.txt script is written, example "DatasetTrainDir"

After this, the scripts loads the first 30 seconds of the whole audiofile, try to detect the spoken language and starts text to speech analyse. When it reach
a block between 6 and 20 seconds, it splits the audiofile and saves the detected text and the audio file to the DataTrainDir.

# 02. train_models
We want to use DL-Art-School to train the required models. Config and tutorial are coming!
https://github.com/neonbjb/DL-Art-School
TBA

License:
MIT License with Extend "No HARM AI"

Copyright (c) 2022-now Tortoise-TTS- Community 

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

"No HARM AI" means, that generated AI content will be marked by "Content was created by Tortoise-TTS-Community" and that this content is truthful. This is an easy to understand rule and we ask you to follow it, please. We want to demonstrate the potential of AI applications can have without showing these overwhelming DeepFake applications.

Credits:
James Betker (Oringal Author)
OpenAI | Whisper 
FFMpeg | Audio Processing
Pytorch | AI Framework




