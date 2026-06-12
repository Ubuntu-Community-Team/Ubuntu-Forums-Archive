---
title: "Problems with input/recording STAC92xx Analog"
date: 2009-08-04
forum: Hardware
---

### Post by handyguy on 2009-08-04
I am having problems with my input and recording in Ubuntu Jaunty 9.04. I did a normal install and everything has been working fine except for recording. I have a dell 1720 that was originally shipped with vista. I installed 8.10 and had this problem also. Here are the results of some things.
```
arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

```

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 127
  Mono: Playback 84 [66%] [-32.25dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 127 [100%] [0.00dB] [on]
  Front Right: Playback 127 [100%] [0.00dB] [on]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Playback Source',0
  Capabilities: enum
  Items: 'Digital Playback' 'Analog Mux 1' 'Analog Mux 2'
  Item0: 'Digital Playback'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 0 [0%] [0.00dB] [off]
  Front Right: Capture 0 [0%] [0.00dB] [off]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 15 [100%] [22.50dB] [on]
  Front Right: Capture 15 [100%] [22.50dB] [on]
Simple mixer control 'Analog Loopback',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Digital Input Source',0
  Capabilities: enum
  Items: 'Analog Inputs' 'Digital Mic 1'
  Item0: 'Digital Mic 1'
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic'
  Item0: 'Mic'
Simple mixer control 'Mux',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 4
  Front Left: Capture 4 [100%] [40.00dB]
  Front Right: Capture 4 [100%] [40.00dB]
Simple mixer control 'Mux',1
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 4
  Front Left: Capture 4 [100%] [40.00dB]
  Front Right: Capture 4 [100%] [40.00dB]
Simple mixer control 'PC Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 3
  Mono: Playback 0 [0%] [-18.00dB] [off]

```
Please help me i really love ubuntu but no sound input really sucks for games in wine and for skype.

---

### Post by abddu on 2009-08-05
I just got my Mic working after noticing that it wasn't while trying to  ... It needs some configuration

Best way is to get Audacity installed, at least it will help in solving this problem since it seems you're sound is working fine, but it just needs some configuration and set-up ...

sudo apt-get install audacity 

Start audacity, and start to record, if you can, then you're done!
else 
Run audacity , Then check the preference in under:
Edit -> Preferences 

try to change the recording options, and try them , as we dont know what exactly is in there ... 

During this, make sure you have the volume controller having the recording options, do this as in the following ...

double-click on the speaker button at top-right corner, near calendar. 

Then [ Edit -> preferences -> add your capture devices, add digital (as in some examples) these are all Dependant on your system ... but make sure you have a source which will appear in the mixer ... from what you've posted it seems there ... just double-check ... coz i only got it working after staying there sometime ... 

You'l then see a recording toolbar in you're mixer ... 

These are the most things which will get you working with a Mic , the problem is to solve the problem we need a similar model or specs ... 

hope this helps in anyway ... 

so next step will try to get a laptop similar to that! which is the only way to give a step by step post ..  


if u do alot of recording and media-related stuff ... check Ubuntu studio ... it may help you

---

### Post by handyguy on 2009-08-06
> **abddu said:**
> I just got my Mic working after noticing that it wasn't while trying to  ... It needs some configuration

Best way is to get Audacity installed, at least it will help in solving this problem since it seems you're sound is working fine, but it just needs some configuration and set-up ...

sudo apt-get install audacity 

Start audacity, and start to record, if you can, then you're done!
else 
Run audacity , Then check the preference in under:
Edit -> Preferences 

try to change the recording options, and try them , as we dont know what exactly is in there ... 

During this, make sure you have the volume controller having the recording options, do this as in the following ...

double-click on the speaker button at top-right corner, near calendar. 

Then [ Edit -> preferences -> add your capture devices, add digital (as in some examples) these are all Dependant on your system ... but make sure you have a source which will appear in the mixer ... from what you've posted it seems there ... just double-check ... coz i only got it working after staying there sometime ... 

You'l then see a recording toolbar in you're mixer ... 

These are the most things which will get you working with a Mic , the problem is to solve the problem we need a similar model or specs ... 

hope this helps in anyway ... 

so next step will try to get a laptop similar to that! which is the only way to give a step by step post ..  


if u do alot of recording and media-related stuff ... check Ubuntu studio ... it may help you

sorry i tried what you said but it still didnt work

---

