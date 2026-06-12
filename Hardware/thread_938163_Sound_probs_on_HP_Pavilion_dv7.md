---
title: "Sound probs on HP Pavilion dv7"
date: 2008-10-04
forum: Hardware
---

### Post by fisfia on 2008-10-04
Hi,

I have a new HP Pavilion dv7 on which I have installed Ubuntu 8.04. The sound is the problem. Its not working. What I have tried to do is to install new alsadrivers. But that did not help. 

What happens is that when I come to the login screen the Ubuntu Welcome sound is played like 10-15 times and with a diminuendo. 

What to do? 
Thanx :D 

PS. The name of the soundcard is (I THINK) HD audio controller. At least that what lspci said. I can post more from lspci if someone need to see. DS.

---

### Post by markbuntu on 2008-10-04
Try my guide here, there are links for hda issues and just about every other problem but do the try this first part first:


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by Tak11 on 2010-03-12
> **markbuntu said:**
> Try my guide here, there are links for hda issues and just about every other problem but do the try this first part first:


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

I have this same issue, and nothing in this guide helped, the sound works however its all muffled and low quality, and my audio mixer only shows an input/output channel, nothing else.

---

### Post by PumpkinSonnema on 2010-03-18
Ditto to the muffled sounds.  This laptop has a subwoofer in addition to the normal speakers.  It appears to be using just the subwoofer.  

I've tried changing some of the devices to use in the Sound Preferences, but it doesn't seem to help.  I'm afraid to poke around with the configs too much since that usually leaves me with no sound and in need of a reinstall.

---

### Post by Tak11 on 2010-03-19
> **PumpkinSonnema said:**
> Ditto to the muffled sounds.  This laptop has a subwoofer in addition to the normal speakers.  It appears to be using just the subwoofer.  

I've tried changing some of the devices to use in the Sound Preferences, but it doesn't seem to help.  I'm afraid to poke around with the configs too much since that usually leaves me with no sound and in need of a reinstall.

yeah, i tried messing around with devices in the alsa config, however no luck either :/

---

### Post by Tak11 on 2010-03-29
A new update fixed the issue. thanks ubuntu :D

---

