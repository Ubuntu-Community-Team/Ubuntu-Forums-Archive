---
title: "Sound output for headphone not working"
date: 2010-08-24
forum: Hardware
---

### Post by YellowDuck on 2010-08-24
Hi all,

headphones on my laptop does not work. When the headphones are plugged in the sound is still comming from the speakers. The microphone instead works very well.
Here follows the sound card type that I have installed on my computer:

ICH4 - Intel ICH6 Intel ICH6 with AD1981B at irq 21

this is a copy & paste of the 'cat /proc/asound/cards' command output. I hope this was the right thing to do.
My laptop is an HP Compaq nx6110.

Thank You,

Eleonora

---

### Post by lidex on 2010-08-26
Try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=hp 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

If no help, then Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
If karmic or earlier, reference the Ubuntu-Bug Audio link in my sig.

---

### Post by YellowDuck on 2010-08-26
your answer is a good solution to my problem.

Thank You.

---

### Post by lidex on 2010-08-26
You're welcome. Please mark the thread solved using 'Thread Tools' up top.

---

