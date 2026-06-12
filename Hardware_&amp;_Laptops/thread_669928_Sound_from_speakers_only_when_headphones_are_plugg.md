---
title: "Sound from speakers only when headphones are plugged in"
date: 2008-01-16
forum: Hardware &amp; Laptops
---

### Post by lwylie on 2008-01-16
Hi Everyone,

I've got a strange one for you.  I recently complied and installed the latest alsa 1.0.15 drivers hoping to get my laptop speakers to mute when my headphones are plugged in using the HDA Intel chipset.  Well after successfully compiling and installing I restarted *with* headphones plugged in.

Apparently that was a mistake.  My speakers now mute, but mute when my headphones are *not* plugged (basically the opposite of what I was hoping to do).  I tried performing a "make uninstall" on the driver, lib, and util sources; and then reinstalled... no luck.

So either:

A)  The alsa 1.0.15 drivers aren't working properly for HDA Intel chipsets.  This is dubious since I'm the only one with this problem on the forums so far.

B)  There is some kind of config file made on the first-time boot of alsa that records the headphone plug state is and then assumes that they are not plugged in.  If so does anyone know where a file like this would be and how to remove it?

Thanks!

---

### Post by lwylie on 2008-01-17
Well I thought that may have been a possibility too so I booted over to Windows and the jack works appropriately.

---

### Post by lwylie on 2008-01-17
Ok... I've tried quite a few things attempting to "uninstall" alsa and get back to my original default Ubuntu state. Does anyone know how to properly uninstall a compiled alsa distribution and get back to the alsa set that came with Ubuntu?

---

### Post by Dynaflow on 2008-01-17
I had a similar problem, and I guess I kept missing a crucial step somewhere in the compiling and configuration process detailed in [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto").

I got lazy and desperate, and I used the script I found here: [http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html]("http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html").  It worked on my Compaq, at the very least.

[EDIT:] Actually, take a look through [this]("http://ubuntuforums.org/showthread.php?t=205449") first.

---

