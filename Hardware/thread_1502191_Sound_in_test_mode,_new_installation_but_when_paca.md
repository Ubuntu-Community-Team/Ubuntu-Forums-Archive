---
title: "Sound in test mode, new installation but when pacakge update, no sound!"
date: 2010-06-05
forum: Hardware
---

### Post by Lapp-Same on 2010-06-05
I have sound on my Fujitsu Siemens Amilo, when i run Ubuntu from the CD and when its new installed BUT after the restricted driver for the grapic card, and the package manager have updated, and my laptop has re-started there is no sound anymore....

---

### Post by dino99 on 2010-06-05
install paprefs and gnome-alsamixer (set your prefs with it)

---

### Post by lidex on 2010-06-06
Try re-installing alsa or just upgrade it using the alsa-upgrade link in my sig. Check your mixer levels as well.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

---

### Post by Lapp-Same on 2010-06-06
> **dino99 said:**
> install paprefs and gnome-alsamixer (set your prefs with it)

Have installed both of them, and checked my settings, and everything locks fine, but still no sound...

and i think this is kinda weird because i have sound in test mode (running from CD)

---

### Post by Lapp-Same on 2010-06-06
> **lidex said:**
> Try re-installing alsa or just upgrade it using the alsa-upgrade link in my sig. Check your mixer levels as well.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

Done, done, done and done :P but no sound! =(

---

### Post by lidex on 2010-06-06
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model= fujitsu 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

---

### Post by Lapp-Same on 2010-06-06
> **lidex said:**
> Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model= fujitsu 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.


The Alsamixer "table" is just empty and when i hit Properties it just wanish and noting happens...
and stil without sound...

---

### Post by lidex on 2010-06-06
Ooops. Looks like a typo on my end. There should be no space between '=' and 'fujitsu'

---

### Post by Lapp-Same on 2010-06-07
> **lidex said:**
> Ooops. Looks like a typo on my end. There should be no space between '=' and 'fujitsu'

Beautifull my friend! never heard so good sound my entire life :D :D

---

### Post by lidex on 2010-06-07
Great! Please mark the thread as solved using 'Thread Tools' up top.

---

