---
title: "Microphone combo jack not working on my netbook"
date: 2010-06-05
forum: Hardware
---

### Post by bivouak on 2010-06-05
Hi,

I have a HP DM1 Pavillon,
[http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=ca&docname=c01935879](http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=ca&docname=c01935879)

with a "Headphone-out/Microphone in combo jack", that means that the netbook has **a single jack for the headphone and microphone** instead of the green and pink jacks.

**The microphone function of the jack doesn't work** with Ubuntu (9.10 karmic koala & 10.04 Lucid lynx), I tried to record sound from this jack with **Audacity,** tried to manipulate the parameters of **alsamixer,**
but no way to make it work.

Any ideas?

thanks guys!

###############
Ubuntu 10.04 Lucid lynx, HP Pavilion dm1, Bi-core 1.30 GHz Intel Pentium Celeron

---

### Post by lidex on 2010-06-06
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by bivouak on 2010-06-06
Hi,

my netbook is  a HP Pavillon DM1-1110ef.

Here are the results  (were in my language, I translated) of the commands you suggested:

```

uname -a

Linux sancy 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux

``````

aplay -l

**** List of PLAYBACK devices ****
carte  0: Intel [HDA Intel], device 0 : STAC92xx Analog [STAC92xx Analog]
  Subdevice: 0/1
  Subdevice: #0: subdevice #0
carte  0: Intel [HDA Intel], device 3 : INTEL HDMI [INTEL HDMI]
  Subdevice: 1/1
  Subdevice: #0: subdevice #0

``````

 cat /proc/asound/version

Advanced Linux Sound Architecture Driver Version 1.0.21.

``````

head -n 1 /proc/asound/card*/codec#*

==> /proc/asound/card0/codec#0 <==
Codec: IDT 92HD81B1X5

==> /proc/asound/card0/codec#1 <==
Codec: Intel G45 DEVCTG

```Many thanks for this help!!

---

### Post by lidex on 2010-06-06
Try an alsa upgrade via the link in my sig. Then go to gnome-alsamixer.
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

### Post by bivouak on 2010-06-07
Thanks!

I made the alsa upgrade with success,
but I still have two symptoms, when using *audacity* or *sound recorder* for exple:
1/ the microphone keeps working all the time
2/ the combo-jack refuses to work as a line-in jack

I also get this message when I use the "Mic Jack Mode" button:
```
** (gnome-alsamixer:1856): WARNING **: gam_toggle_set_state (). No idea what to do for mixer element "Mic Jack Mode"!
```Keep doing a few tests....

---

### Post by lidex on 2010-06-07
This could/should/may work. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=intel 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
No help, try these other possible models (only one at a time please):
```
hp-m4
hp-hdx
hp-dv5
```

---

### Post by bivouak on 2010-06-10
Sorry lidex,
what do you mean by "Check your levels in alsamixer"?
I use alsamixer, then I go to the "Capture" section, I have 4 bars (Front Mic, Mic, Capture, Digital).
I manage to switch off the microphone by changing the status of the Capture bar (the red "L R"),
but still no way to make my computer understand that the jack is a line-in source....
(if I plug a source in the jack, no more sound in the speakers since the system switch to the "headphone" mode)
Crazy!
Thanks again for your help!

---

