---
title: "Inbuilt Mic on Acer Extensa 5220"
date: 2008-07-30
forum: Hardware
---

### Post by bobdobbs on 2008-07-30
Hi All.

Much to my surprise, installing ubuntu on my first laptop - an acer extensa 5220 - was pretty easy. However, I do have a couple of issues, one of which is getting the inbuilt mic to work.

When I test the mic, using the application in 
Applications -> Sound and Video -> Sound Recorder, I am presented with a number of possible devices to record from - Front Mic Boost, Mic, Capture, Capture 1, Digital.

I guess only Mic and Front Mic Boost concern me.

When I play back what I have recorded, I just get a weird digital grating sound.

What is going on here? How can I fix this and get sound?

Thanks.

---

### Post by Guyik on 2010-05-16
Hi, I had the same problem until today.

I tried with this:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

First of all you have to disconnect both captures by executing alsamixer in a terminal and turn off everything except "front".

Afterwards, follow the instructions on the link above.

It have worked to me (Acer Extensa 5220, Intel Celeron, 2Gb RAM, Realtek ALC268 ), I hope it works to everyone.

Notes:
* You will have to select the input device by executing "alsamixer" in a terminal and pressing F4:
Front Mic = the microphone near the webcam (if it exists).
Mic = the red input where the microphone wire is connected.
Line = the blue input, I think.
CD = no idea.

* You will hear noise unless you adjust gain correctly. This means you cannot turn up "capture", "digital" or "front mic" a lot in alsamixer because you hear a constant "crak, crak".

---

### Post by lidex on 2010-05-16
You may also need to do this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=acer 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

---

