---
title: "Sound issues with Cirrus Logic CS4610"
date: 2005-01-16
forum: Hardware &amp; Laptops
---

### Post by schleyfox on 2005-01-16
I have an old IBM thinkpad laptop.  It has a Cirrus Logic CS4610 sound card.  The ALSA soundcard matrix shows it as supported with "cs46xx".  I have manually configured many  soundcards on my various Gentoo boxen, but I do not even know where to start in ubuntu.
Output from lspci | grep -i audio

0000:00:06.0 Multimedia audio controller: Cirrus Logic CS 4610/11 [CrystalClear SoundFusion Audio Accelerator] (rev 01)

Your help is appreciated.  Thank You.

---

### Post by yarri on 2005-07-05
Hi!

I have similar problem - there is no sound at all. 

lspci | grep -i audio
0000:00:0b.0 Multimedia audio controller: Cirrus Logic CS 4610/11 [CrystalClear SoundFusion Audio Accelerator] (rev 01)

Unfortunately I am still newbie - so I have not even slightest idea how to force my box to make sound



                                                       Thanks in advance

                                                                         Yarri

---

### Post by Michael R Head on 2005-08-09
The alsa driver seems to barf on the thinkpad's chip. Thankfully, the old OSS drivers are still available. Edit /etc/hotplug/blacklist.d/alsa-base and change the line "cs46xx" to "snd-cs46xx" and hotplug should automatically load the OSS driver.

---

### Post by Leena on 2005-08-10
I guess I have quite a similar problem. I installed Kubuntu 5.04 to an old Siemens Xpert PC  with V65MA motherboard.  Everything's is running smoothly  .. expect no sound. As far as I know there is a CS4610 sound card, too.

Unfortenately, there is no /etc/hotplug/blacklist.d/alsa-base in my system  :roll: 

Leena N

---

### Post by Tiede on 2005-08-10
[QUOTE=Leena]I guess I have quite a similar problem. I installed Kubuntu 5.04 to an old Siemens Xpert PC  with V65MA motherboard.  Everything's is running smoothly  .. expect no sound. As far as I know there is a CS4610 sound card, too.

Unfortenately, there is no /etc/hotplug/blacklist.d/alsa-base in my system  :roll: 

Leena N[/QUOTE]
 I think the file you are looking for is /etc/hotplug/blacklist.d
it's a text file that blocks some modules from loading at startup.

---

### Post by afrifreak on 2005-11-04
Hi there,

I have even a weirder problem with my sound card, a Hercules Gamesurround Fortissimo III. It works with the cs46xx module, but only sometimes. When I boot my box the first time of day, the sound is very distorted and coming from one speaker. The other speaker produces only rubble. But, when I just reboot, the sound just works! 
Lspci shows my card, I get no error messages but still there is a problem. 
Anyone an idea?

Andres

---

