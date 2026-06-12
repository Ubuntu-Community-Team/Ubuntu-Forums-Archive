---
title: "Microphone doesnt work on Jaunty"
date: 2009-05-09
forum: Hardware
---

### Post by madHatterCutsTheChatter on 2009-05-09
***Hardware**:*
Vaio FW140E, 2.2ghz, 3gb RAM, 250 gb HDD with built in mic & webcam.

***OS**:* 
Jaunty 32bit

***Problem**:*
Microphone doesnt work. I have tried a number of programs like Sound Recorder, Audacity, Empathy Messenger. I cant record or no1 can hear me.

I have tried both PulseAudio and Alsa Mixers with all volumes set to max.

Additionally on Alsa setting the Mic boost volume > 50% just creates a uniform noise from the speakers & that is all that gets recorded.

(Webcam works: i tried it with Cheese Webcam Booth)

---

### Post by Rhemat on 2009-11-09
I'm having the same issue.  I figured it could be that I have three audio devices (onboard [disabled], video card, and audio card), but I selected my audio card.  Gnome Sound Recorder locks up when I try to record on my desktop (but not on my laptop, using Xubuntu 8.10).  Audacity doesn't pick up anything, and stops attempting to record after a second.  Any ideas?

---

### Post by bbqau on 2009-11-10
I am also having the same problem. Is there a module of some kind or some hardware configurations that need to be set ? I figure that the correct sound input/output is set and its detecting my sound card ( not onboard ) as outbound sound is working, its just my microphone is not. I wish to use Skype and do some screencasts using gtk-recordMyDesktop however i currently am unable to. 

I am on 9.10 Karmic Koala

---

### Post by gradinaruvasile on 2009-11-10
> **madHatterCutsTheChatter said:**
> ***Hardware**:*
Vaio FW140E, 2.2ghz, 3gb RAM, 250 gb HDD with built in mic & webcam.

***OS**:* 
Jaunty 32bit

***Problem**:*
Microphone doesnt work. I have tried a number of programs like Sound Recorder, Audacity, Empathy Messenger. I cant record or no1 can hear me.

I have tried both PulseAudio and Alsa Mixers with all volumes set to max.

Additionally on Alsa setting the Mic boost volume > 50% just creates a uniform noise from the speakers & that is all that gets recorded.

(Webcam works: i tried it with Cheese Webcam Booth)

In alsamixer (the terminal version).
Press tab to navigate the 3 views (tabs). Go to the capture tab.
Do u have "CAPTUR" written on some device? (like in the screenshot i attached). Also, at the "Input so" devices (as in the screehshot) what options u have? U can navigate the devices with the arrow buttons (left-right move, up/down increase/decrease volume or cycle options).

Do this while recording, the settings apply real time. Also, on the sound options u should see the mic input levels (the right-preferences menu on the sound tray icon) - check those if are not muted somehow.

---

### Post by Rhemat on 2009-12-24
Of course, in alsamixer, mine is only detecting the audio of my ATi Video card.  Is there a way I can tell it to not pay attention to that cards audio processor?
Thanks for your help.

============
I noticed after posting, that in Gnome-Sound-Recorder, it doesn't list what device it is recording from, or a place to select recording device.  Anyone else have this bug before?

---

