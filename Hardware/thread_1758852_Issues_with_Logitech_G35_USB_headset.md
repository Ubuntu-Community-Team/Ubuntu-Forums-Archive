---
title: "Issues with Logitech G35 USB headset"
date: 2011-05-15
forum: Hardware
---

### Post by frozenblwf on 2011-05-15
Howdy! I am a brand spanking new Linux inductee running Ubuntu 11.04. My issue stems from my USB headset. It is listed in the "Hardware" tab in the sound preferences, however it is not listed in "Input" or "Output" tabs. If I click on "Test speakers" with the headset highlighted in the Hardware tab, the window closes out without displaying the audio test. The audio test works fine on my listed desktop audio speakers. 

I know the headset is good because I can use it on Virtualbox in a windows xp environment. Here is what I have tried so far : 

Booting and logging in with the headset connected
Installed gnome-alsamixer. The headset is under the usb mixer tab but I an unable to select it for output
Installed Alsamixer
Installed pavucontrol - this program again sees the headset but cannot output audio to it

I ran a test by using the command "ubuntu-bug audio" and during the info gathering it played sound through my headset with no problems. 

So I am unsure of what to try for this. Is my headset not compatible? How do I make it appear in the "input and output" tabs so I can listen to music on my headset? Thanks!

---

### Post by frozenblwf on 2011-05-15
Bumping for afternoon crowd =)

---

### Post by joopbraak on 2011-06-01
What happens if you :

- close sound preferences
- kill the pulseaudio process in the system monitor
- press Alt+F2 and run pulseaudio
- open up sound preferences

Is the headset listed now in the input/output tab ?

---

### Post by perlon on 2011-06-02
> **joopbraak said:**
> What happens if you :

- close sound preferences
- kill the pulseaudio process in the system monitor
- press Alt+F2 and run pulseaudio
- open up sound preferences

Is the headset listed now in the input/output tab ?

Thank you, I had the same problem and this works.
Anyway it looks like pulseaudio has an auto-restart function, so step 3 is not necessary.

---

### Post by Scoobin on 2011-06-11
Thanks! This fixed mine too! :)

---

### Post by Foosvald on 2011-06-18
> **joopbraak said:**
> What happens if you :

- close sound preferences
- kill the pulseaudio process in the system monitor
- press Alt+F2 and run pulseaudio
- open up sound preferences

Is the headset listed now in the input/output tab ?
Had to register just to say thanks. Thank you! :D

---

