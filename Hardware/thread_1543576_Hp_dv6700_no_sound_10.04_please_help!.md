---
title: "Hp dv6700 no sound 10.04 please help!"
date: 2010-08-01
forum: Hardware
---

### Post by DaBurr on 2010-08-01
Hi everyone, i recently installed Ubuntu 10.04 on an 2 year old hp 6700, which was running vista, and everything went smoothly, i realized my sound does not work, everything else worked out,  i then found this tip and tried it out in the terminal 
sudo apt-get install linux-backports-modules 

the sound came back, only for few hours, only to find out it stopped working all
over again. Now i dont know what else to do or try i even reinstalled
Ubuntu and still no sound, the sound icon just has this next to it ---
my computer is a AMD system

Laptop Specs

HP DV6700

CPU: AMD Turion 64 x2 2.0ghz

Motherboard/chipset geforce 7150/nforce 650
ram: 3gb
hdd: 200gb


if you guys know anything i cound try please help, i would be truly thankful!

---

### Post by lidex on 2010-08-01
Try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=dell-m4-3 enable_msi=1 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

No joy? Change that previous entry to this and reboot:
```
options snd-hda-intel model=hp-dv5 enable_msi=1
```

---

### Post by DaBurr on 2010-08-02
Thank you so much! That did it, i was seriously little skeptical that it would work, once i rebooted, the ubuntu startup sound came on , and the alsa mixer shows the value working. Thank you very much!

---

### Post by lidex on 2010-08-02
One down, a million to go. ;)
If you would please, mark the thread as solved using 'Thread Tools' up top.

---

### Post by korifey13 on 2011-06-18
> **lidex said:**
> No joy? Change that previous entry to this and reboot:
```
options snd-hda-intel model=hp-dv5 enable_msi=1
```
This works for my HP Compaq nx6325. Thanks a lot!

---

