---
title: "Sound on Toshiba Satellite A205-S4587"
date: 2008-01-28
forum: Hardware &amp; Laptops
---

### Post by cnlevo on 2008-01-28
I recently installed ubuntu 7.10 dekstop on my laptop (a205-s4587) and i've got everything working correctly but sound. I thought i found a thread that would help me, but after i got done with that my sound is completely screwed...before i wasn't getting any sound but it said it had the right drivers installed.

Does anyone know how to help me get this up and running. I am all about learning and doing things on my own but i'd love to get some help with getting my sound up. i need it bad. sound and wifi is the one thing i couldn't go without. i got the modem drivers done fine, but i can't get sound.

Any help would be appreciated. If you need any info lmk. terminal says i have realtek ID 268 sound. So maybe that helps too. I don't know.

---

### Post by xc3RnbFO8P on 2008-01-28
Try to install linux-backports-modules-generic in Synaptic Package Manager.

---

### Post by cnlevo on 2008-01-28
ok, imma give that a shot.

i got another problem now.

ALLLLL my icons on the taskbar have disappeared. I made sure they were all enabled and i've restarted. I can add them as applets, but they don't work with the right theme i'm using.. (mac4lin) it is just a normal icon if i add it from the "add to panel" thing.

---

### Post by arriagga on 2008-03-24
can you please tell me how to make the modem work.

thanks

> **cnlevo said:**
> I recently installed ubuntu 7.10 dekstop on my laptop (a205-s4587) and i've got everything working correctly but sound. I thought i found a thread that would help me, but after i got done with that my sound is completely screwed...before i wasn't getting any sound but it said it had the right drivers installed.

Does anyone know how to help me get this up and running. I am all about learning and doing things on my own but i'd love to get some help with getting my sound up. i need it bad. sound and wifi is the one thing i couldn't go without. i got the modem drivers done fine, but i can't get sound.

Any help would be appreciated. If you need any info lmk. terminal says i have realtek ID 268 sound. So maybe that helps too. I don't know.

---

### Post by captainsquinty on 2008-04-06
cnlevo,

I also have a Toshiba A205, I fixed my sound with the info here:
[https://bugs.launchpad.net/alsa-driver/+bug/116326](https://bugs.launchpad.net/alsa-driver/+bug/116326):

I followed the directions in this post
[https://bugs.launchpad.net/alsa-driver/+bug/116326/comments/137](https://bugs.launchpad.net/alsa-driver/+bug/116326/comments/137)

which uses drivers from the realtek site noted in the above post:
[https://bugs.launchpad.net/alsa-driver/+bug/116326/comments/134](https://bugs.launchpad.net/alsa-driver/+bug/116326/comments/134)

I then used the instructions here:
[http://taufanlubis.wordpress.com/2007/11/26/fix-no-sound-for-ubuntu-in-toshiba-satellite-a205-s4707/](http://taufanlubis.wordpress.com/2007/11/26/fix-no-sound-for-ubuntu-in-toshiba-satellite-a205-s4707/)

Specifically, I added:  
options snd-hda-intel model=toshiba

to my /etc/modprobe.d/alsa-base, and then got the "magic packages" (for gutsy):
 apt-get install linux-backports-modules-generic

[edit] for hardy, i'm not sure which ones to get, i think its
linux-backports-modules-hardy-generic, or
linux-backports-modules-hardy

It worked after a reboot.

Good luck!

---

