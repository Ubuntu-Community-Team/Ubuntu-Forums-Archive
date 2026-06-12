---
title: "sound problems with feisty 7.04"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by greenie9 on 2007-04-20
ive updated my laptop from edgy to fiesty and now nothing seems to want to obey the "master sound"

i can mute my PC, then open up VLC and the sound still plays through my speakers

it has the audio Intel 82801G (ICH7 Family) (rev 02) sound card, and i re-installed the alsa drivers, and then did alsaconf, but this had no affect, any/all help would be greatly appreciated!!!

---

### Post by kukibl on 2007-04-22
I have the same sound card on my laptop, sound works properly but the quality is awful, I can barely hear it (it also happended after Edgy>Feisty upgrade). I have both - Ubuntu and Arch on my laptop, and the same problem is on Arch, after recent update. I guess the problem is in kernel, so it is probably the best thing to wait for some patch.:(

---

### Post by tomazela on 2007-04-22
i'm having problems with sound too.
i have updated my laptop from edgy to feisty, and the sound stop working.
so, i decided to reinstall ubuntu formating the hd before, but the problem remains.

---

### Post by kukibl on 2007-04-23
Try this:

$sudo gedit /etc/modprobe.d/alsa-base

Add the following line add the end of the file:

options snd-hda-intel model=auto

It worked for me...:)

---

### Post by dustman on 2007-04-23
yep...same problem here... :(...sound worked perfectly under edgy, but when I upgraded to feisty it died .... I have a Toshiba A100-529 laptop.

---

### Post by greenie9 on 2007-04-24
i found that it had changed what the volume control modified...

it seems the sound now modifies the CD rather than PCM

right click on the volume icon and select preferences and select PCM!!!

(still working on making the sound buttons on laptop work :P)

---

### Post by mikey on 2007-04-24
Re: sound problems with feisty 7.04
Try this:

$sudo gedit /etc/modprobe.d/alsa-base

Add the following line add the end of the file:

options snd-hda-intel model=auto

It worked for me...
Reply With Quote

worked for me as well. thanks!

---

