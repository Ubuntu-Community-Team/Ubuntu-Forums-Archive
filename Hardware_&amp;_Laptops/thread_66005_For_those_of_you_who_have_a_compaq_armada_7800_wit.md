---
title: "For those of you who have a compaq armada 7800 with no sound...."
date: 2005-09-15
forum: Hardware &amp; Laptops
---

### Post by qb4ever on 2005-09-15
I running ubuntu 5.04 hoary

I just got finished installing ubuntu for the first time and found that the sound card (ESS 1879 Plug and play WDM) just wouldn't work after a few hours of tweaking.

I found this: 
[https://www.redhat.com/archives/fedora-list/2004-November/msg02510.html](https://www.redhat.com/archives/fedora-list/2004-November/msg02510.html)

and made a few changes to it...

First start up the x server and open a terminal then type:

modprobe snd-es1688 port=0x220 mpu_port=0x388 irq=5 dma8=1

it should sit for a few seconds and go back to the prompt. 

Then start type ESD to start the sound system

open the volume control and unmute, etc.  and the sound should work.
then to have it load on startup:

modprobe snd-es1688 >> /etc/modules
if the above command doesn't work use your favorite editor and add "snd-es1688" minus the quotes  to /etc/modules


edit: also if the sound card is found and no sound is being produced read this thread: 
[http://www.ubuntuforums.org/showthread.php?t=8882&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=8882&page=1&pp=10)

---

### Post by dieselpower on 2005-10-16
Thank you! It worked perfectly on my armada 7400. Now I can watch DVD's again.

---

### Post by mckemie on 2006-11-29
Doesn't work with Edgy! Here are the first couple of error messages:
---
root@ubuntu610c:/usr/local/bin# modprobe snd-es1688 port=0x220 mpu_port=0x388 irq=5 dma8=1
FATAL: Error inserting snd (/lib/modules/2.6.17-10-generic/kernel/sound/core/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
---

---

### Post by mckemie on 2006-11-29
Spoke too soon!  It just didn't want to see all those parameters.  Just
modprobe snd-es1688
works!

BTW, for those of you having xmms trouble, just search the forums for "double size xmms".

---

### Post by Toshibi on 2007-12-11
This works for Gutsy too!

---

