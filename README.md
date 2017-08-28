@jarbas fork of mycroft that works in the browser. You can text in the browser and get text and audio back.

https://github.com/JarbasAI/JarbasAI

## 1. Install
```
cd ~/mycroft-core
git remote add jarbas git@github.com:JarbasAI/JarbasAI.git
git pull --all
git checkout -b patch-15
git merge jarbas/patch-15
./build_host_setup_ubuntu.sh
./dev_setup.sh
```

## 2. Tweak
Modify 2 files:

1. requirements.txt: remove pyautogui near the bottom
2. mycroft/configuration/jarbas.conf:
replace user and password and change module to ibm

change      "module": "pocketsphinx",
to
"module": "ibm",


## 3. Run
./mycroft.sh start
./start.sh webchat


## 4. Troubleshoot

### if you get this:
  Command "python setup.py egg_info" failed with error code 1 in /home/oren/t/pip-build-zRRGDT/pyautogui/
  Warning: Failed to install all requirements. Continue? y/N
  i got this error during ./dev_setup.sh
  go to requirements.txt and remove pyautogui near the bottom
  hat is for the vocal desktop control skill, i havent figured out why it fails yet

### replace mycroft STT
  https://console.bluemix.net/
  they give you 30day free
  to try speech to text
  you cna later use google which offer 1 free year
  this one is faster just to show you how to set things up
  catalog/speechto text. keep the default. hit 'create'
  https://console.bluemix.net/services/speech_to_text/9471275d-304d-4d7c-8587-8c96c8b2b749/?paneId=credentials&env_id=ibm%3Ayp%3Aus-south
  go to 'service credentials'
  and user/password to mycroft/configuration/jarbas.conf
  change      "module": "pocketsphinx",
  to
  "module": "ibm",


### make sure there are 6 screen sessions
screen -list
10873.mycroft-voice     (08/27/2017 03:02:02 PM)        (Detached)
screen -r 10873 - voice log
also useful - skills log
troubleshoot: ./start.sh audio

## 5. Notes

its because of firefox, its same as debian but firefox in debina is called firefox-esr
replace mycroft STT
you must use some external one
i also use snowboy, so you can have many names at once  its lighter than pocketsphinx you may want to train your onw in snowboy.kitt.ai
i left examples and comments in the config file
mycroft/configuration/jarbas.conf
in there go to "stt"
and input your API keys
i used ibm

@jarbas has a fork that works on the browser. you can text mycroft and see it in the browser.
Audio is possible as well but a bit hard: Just gotta handle grabbing audio in the browser, and passing it to MC. Could be complex


### skills
in mycroft-core/jarbas_skills

## 6. try
random image
kill with: screen -r 10202.mycroft-display, ctrl+c
sing a song. stop
tell me a joke
news
how are you?
record
stop recording

