
# VoiceBot [![MIT License](https://img.shields.io/badge/License-MIT-green.svg)](https://choosealicense.com/licenses/mit/)

A neural network voice model that executes commands on demand, like a voice assistant, but very crude


## Authors

- [@xsvebmx](https://www.github.com/xsvebmx) 



## Demo

Insert gif or link to demo


## Screenshots

![App Screenshot]([https://git](https://github.com/xsvebmx/VoiceBot/blob/main/demo.png))


## Run Locally

Clone the project

```bash
  git clone https://link-to-project
```

Go to the project directory

```bash
  cd my-project
```

Install dependencies

```bash
  npm install
```

Start the server

```bash
  npm run start
```


## Usage/Examples

```python
import json, pyaudio
from vosk import Model, KaldiRecognizer

model = Model('vosk-model-small-ru-0.4')
rec = KaldiRecognizer(model, 16000)
p = pyaudio.PyAudio()
stream = p.open(format=pyaudio.paInt16, channels=1, rate=16000, input=True, frames_per_buffer=8000)
stream.start_stream()

def listen():
	while True:
		data = stream.read(4000, exception_on_overflow=False)
		if (rec.AcceptWaveform(data)) and (len(data) > 0):
			answer = json.loads(rec.Result())
			if answer["text"]:
				yield answer["text"]

for text in listen():
	if text == "кеша":
		print("Hello")
	elif text == "пока":
		quit()
	else:
		print(text)
```


## Tech Stack

**Client:** React, Redux, TailwindCSS

**Server:** Node, Express


## Features

- Light/dark mode toggle
- Live previews
- Fullscreen mode
- Cross platform


## Environment Variables

To run this project, you will need to add the following environment variables to your .env file

`API_KEY`

`ANOTHER_API_KEY`


## Documentation

[Documentation](https://linktodocumentation)

