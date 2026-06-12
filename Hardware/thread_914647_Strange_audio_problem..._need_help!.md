---
title: "Strange audio problem... need help!"
date: 2008-09-09
forum: Hardware
---

### Post by JECHO on 2008-09-09
Hey guys i just got a new dell latitude  e6400 and everythings great except my audio. the audio works and sounds great.


PROBLEM: even though i have audio when i try muting or raising/lowering the volume (either with the shortcut keys or the volume applet on the gnome panel) the sound level does not change...

i have investigate dand found what is happening:

the volume meter in the volume applet controls the master volume. in order for my volume levels to change i have to use the PCM sliders. The masters dont do anything. :(

anyone have any ideas??? :confused:

---

### Post by JECHO on 2008-09-10
bump!

anyone? :-/

---

### Post by Aramaz on 2008-09-22
I've got the same problem! (Hardy 8.04)

Also, I have a problem with wifi not working, how did you get it working? (Intel(R) WiFi Link 5100 AGN)

In windows the the middle button can be pressed to scroll with the touch point, is there a way to set that up in ubuntu also?

appreciate any help...

---

### Post by JECHO on 2008-09-22
> **Aramaz said:**
> I've got the same problem! (Hardy 8.04)

Also, I have a problem with wifi not working, how did you get it working? (Intel(R) WiFi Link 5100 AGN)

In windows the the middle button can be pressed to scroll with the touch point, is there a way to set that up in ubuntu also?

appreciate any help...


yeah hey i can help you fix the wifi :) look here and follow the instructions: [http://ubuntuforums.org/showthread.php?t=906865](http://ubuntuforums.org/showthread.php?t=906865)

as far as audio... im still lost. same with the touchpad :(

---

### Post by mcallenSchmee on 2008-09-22
Try this: right click the volume icon> select preferences, then choose which track to control. I think this is what worked for me before.

---

### Post by JECHO on 2008-09-22
> **mcallenSchmee said:**
> Try this: right click the volume icon> select preferences, then choose which track to control. I think this is what worked for me before.

yeah ive tried that and no luck :-/

---

### Post by markbuntu on 2008-09-22
Also, you need to make sure that the Volume Control is using the correct device. Right click on the volume control and choose Open Volume Control. The header should be your sound card, if it is not, File/Change Device and choose the correct device. It could be set to your usb webcam mic or something.

Then you can use the Volume COntrol/Preferences to choose which slider is controlled by your multimedia keys and the Volume control.

---

### Post by JECHO on 2008-09-22
> **markbuntu said:**
> Also, you need to make sure that the Volume Control is using the correct device. Right click on the volume control and choose Open Volume Control. The header should be your sound card, if it is not, File/Change Device and choose the correct device. It could be set to your usb webcam mic or something.

Then you can use the Volume COntrol/Preferences to choose which slider is controlled by your multimedia keys and the Volume control.

yeah i tried that too and still no luck, its like the output is jsut getting directed the wrong way... ill get it working eventually... i hope:^o

---

### Post by markbuntu on 2008-09-22
You can try my troubleshooting guide then. I was trying to let you off easy because it is quite long and can get very involved: 

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by Aramaz on 2008-09-23
Jecho> Thanx, now my wireless is working :)

I don't have a docking device, but I could not modify or mute the sound at all before. But changing the device for the volume control I can now change the volume with the volume buttons on the laptop, though not by using the volume slider.

thanx again!

---

### Post by pdub on 2008-10-17
To fix the issue with the volume buttons not working on my Dell E6500 I had to go into System->Preferences->Sound and select front in the Default Mixer Tracks section. The device is HDA Intel (Alsa mixer).

Selecting it from the volume control by right clicking and selecting preferences did NOT work for me.

---

### Post by JECHO on 2008-10-17
> **pdub said:**
> To fix the issue with the volume buttons not working on my Dell E6500 I had to go into System->Preferences->Sound and select front in the Default Mixer Tracks section. The device is HDA Intel (Alsa mixer).

Selecting it from the volume control by right clicking and selecting preferences did NOT work for me.


hey thanks a lot! surprisingly that worked :)


unfortunately i still have an audio problem... after doing what you suggested, the shortcut keys for volume control on my keyboard now work but i only get audio out of the left speaker. and the "master" volume control slider still does not work.

---

