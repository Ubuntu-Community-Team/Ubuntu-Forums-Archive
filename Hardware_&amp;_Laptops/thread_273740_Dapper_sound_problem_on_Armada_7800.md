---
title: "Dapper sound problem on Armada 7800"
date: 2006-10-08
forum: Hardware &amp; Laptops
---

### Post by mckemie on 2006-10-08
On numerous Debian distros and 2.4.x kernels, I have gotten sound to work on my Compaq Armada 7800s (and 7400s) by putting this in /etc/modules:
sb irq=5 io=0x220 dma=1
With Dapper and the 2.6 kernel, sound worked briefly with the above modification, but then no more.  When I attempt to play sound with xmms, aplay, or other, I get the suggestion that my card is not set up properly or that some other software is using it.

I have looked here:
[http://ubuntuforums.org/showthread.php?t=50971&highlight=7800+sound](http://ubuntuforums.org/showthread.php?t=50971&highlight=7800+sound)
and here:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
but I remain in the dark.

It's probably something I don't understand about sound servers or ALSA.  Or something else.  Who can help me?

---

### Post by mckemie on 2006-10-13
Here is a post buy a guy that solved the problem with Breezy:
[http://www.ubuntuforums.org/showthread.php?t=66005&highlight=7800+sound](http://www.ubuntuforums.org/showthread.php?t=66005&highlight=7800+sound)

Alas, where is what I get on Dapper:
root@Ubuntu606-a:~# modprobe snd-es1688 port=0x220 mpu_port=0x388 irq=5 dma8=1
FATAL: Error inserting snd_es1688 (/lib/modules/2.6.15-23-386/kernel/sound/isa/es1688/snd-es1688.ko): No such device
root@Ubuntu606-a:~#

I wonder if the sound card on this particular computer has died?  Does anyone have sound working on an Armada 7400/7800 running Dapper?

---

