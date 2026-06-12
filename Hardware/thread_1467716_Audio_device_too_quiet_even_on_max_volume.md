---
title: "Audio device too quiet even on max volume"
date: 2010-05-01
forum: Hardware
---

### Post by maestrobwh1 on 2010-05-01
Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)

Lucid 64 bit
Kubuntu

The volume maxes out at a MUCH higher volume level in XP than it does with the same device in Ubuntu.  I have PCM set to MAX as well and it seems to have little effect set at 0 or 100.

I installed aumix and have added 

aumix -w 100
aumix -o 100

to a startup script and it helped a bit but not much.

---

### Post by dino99 on 2010-05-01
you need to tweak alsamixer

---

### Post by maestrobwh1 on 2010-05-01
Everything is set to 100 in alsamixer.  It just is half as loud as it is in XP.  Is there a "preamp" thing I can do somewhere?

---

### Post by lidex on 2010-05-02
> **maestrobwh1 said:**
> Everything is set to 100 in alsamixer.  It just is half as loud as it is in XP.  Is there a "preamp" thing I can do somewhere?
On some configurations. Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by maestrobwh1 on 2010-05-02
```
$uname -a
Linux ubuntu-asus-64 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux

$aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
head -n 1 /proc/asound/card*/codec#*

$Codec: Realtek ALC269
```

---

### Post by lidex on 2010-05-02
What is the make/model of your PC/Laptop?

---

### Post by maestrobwh1 on 2010-05-02
It is one of the new Asus EEEPC 1201N models: hybrid between a laptop and netbook I guess: has a 64 bit AMD processor (Neo).  Running 64 bit Lucid Kubuntu.

I looked in your HD-Audo text file sand the ALC269 seems to match my output above.  It does work, just quietly and a few things that are supposed to make sound do not (firefox addon downthemall is supposed to make a sound when a download is finished and that does not happen BUT flash does make sound).

Everything just works pretty well.  Wireless needed a ppa package and I needed to add a grub line for acpi to get the sound Fn keys to work.  The sound level was not changed by this but at least I could use the keys to up and lower and mute the volume.
**EDIT: new kernel version was released and it works much better since today's upgrade.**

---

### Post by lidex on 2010-05-02
You're the maestro. Try this. Install alsa-backports:
```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
``` Now the fun part. Using a Terminal="Applications->Accessories->Terminal"
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
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels.
Go to "System>Preferences>Sound" and make sure the correct soundcard is default.

---

