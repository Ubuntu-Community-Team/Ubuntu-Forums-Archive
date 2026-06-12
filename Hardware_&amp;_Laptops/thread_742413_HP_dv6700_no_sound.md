---
title: "HP dv6700 no sound"
date: 2008-04-01
forum: Hardware &amp; Laptops
---

### Post by CrA86 on 2008-04-01
Hi all, iam new to linux world, i bought the latest linux format magazine, and i love it, so i decided to use linux instead of windows, so i installed ubuntu, but i do not have sound, i searched the net for the solution and i found some but nothing worked for me.

I installed the latest version of alsa, but with no luck.
I tried to install mercurial-1.0 but with no luck too, it say that i don't have gcc but i do?????

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC268 Digital [ALC268 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Iam hoping to help me, to see the power of open-source community.

---

### Post by rfs13286 on 2008-04-02
Hi CrA86

Three weeks ago I bought a new HP dv6760 laptop and at first I was having some issues with ubuntu installation. My main concerns were the sound not working at all (though it did work in windows vista) and no webcam support.

but that all changed once I found the following link:

[https://wiki.ubuntu.com/HP_dv6000_Series](https://wiki.ubuntu.com/HP_dv6000_Series)

There is all sort of useful information for people with laptops from the dv6000 series. Read it carefully and you will find the solution to your problems.

Specifically in regard to sound, the solution was as easy as:

1. enabling ubuntu backports using the System Adiminstration -> software sources
2. reloading the package list
3. downloading the package linux-backports-modules through synaptic
4. rebooting the computer
5. tadaaa all sound normally!!

I cannot guarantee this will work for you because maybe you've been compiling alsa sources. in last resort try reinstalling ubuntu and following my procedure on a fresh install.

Hope this helps

---

### Post by CrA86 on 2008-04-02
Thank you very much, but i solved this problem by myself.
All what i did is installing the latest alsa
and in alsa-base change the model=hp
and everything works fine after the reboot.
I love you ubuntu.

---

