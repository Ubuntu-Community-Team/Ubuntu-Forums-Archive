---
title: "ALC269 Dell Mini Jack Sensing 10.04"
date: 2010-06-05
forum: Hardware
---

### Post by eric2k0 on 2010-06-05
Hi im not exactly new to this but theres a lot that i still dont quite understand so please bear with me. i have a Dell Mini 10 with a Broadcom ALC269 soundcard the speakers work but whenever i plug headphones into the jack sound comes out of the headphones and the speakers im not sure how to fix this if anybody else has any idea how to fix this then there input would be very appreciated thanks in advance

oh and also if its anyhelp i had the jack sensing in 9.04 but 9.10 and 10.04 do not have it working

---

### Post by lidex on 2010-06-06
You might try using gnome-alsamixer to enable jack-sensing. 
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

### Post by eric2k0 on 2010-06-06
Thanks for the help, I installed gnome-alsamixer and when i opened it i went into the soundcard properties menu and i saw all the options of what to enable they were all already enabled but after trying the slides and enabling and disabling the options Im still not having any luck getting the jack sensing working but i did notice one thing when i started the program the headphones option was already enabled but whenever i disable it the sound stops working all together im not sure if thats any help but i thought it might be worth mentioning

---

### Post by lidex on 2010-06-06
OK. Try this then. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=basic 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

If that is no help, try auto instead of basic.

---

### Post by eric2k0 on 2010-06-06
I tried both Auto and Basic models and tried some stuff with the alsamixer i still cant get the jack sensing to work another thing i noticed which might be worth mentioning is the headphone volume in alsamixer is always at 0 (which i guess is normal) but whenever i mute it i still get no volume from the speakers or the headphones, is it possible the computer thinks the speaker are the headphones? anyway just a thought thanks again for the help

---

### Post by lidex on 2010-06-06
Is there a model number for this PC?
These are the options noted on *markbuntu's* snd-hda-intel thread for alsa-base.conf:
```
Dell model=dell
T3400, Vostro 1200 model=dell
XPS 410 model=dell-bios
Dimension E520 model=dell-3stack
Dimension 9150 model=dell-m81
Inspirion 1420n options snd-intel8x0 ac97_quirk=1 buggy_irq=1 enable=1 index=0
options snd-hda-intel model=3stack enable=yes
options snd-hda-intel model=auto position_fix=1 enable=yes
Adamo
options snd-hda-intel model=dell-eq
Dell M1330, model=dell-3stack
dell vostro 1000 / inspirion 1501 model=dell-m23

1526 model=dell-m81
Inspirion 530 model=6stack-dell
desktops model=dell-m4-1 STAC92HD71B
model=dell-m4-2 STAC92HD71B
model=dell-m6 STAC92HD73
model=dell-bios STAC92HD73
Studio 540 snd_hda_intel probe_mask=1 
```

Of course you could always try the basic models, ie: dell, dell-bios, dell-eq, etc.

---

