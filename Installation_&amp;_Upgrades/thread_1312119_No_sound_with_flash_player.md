---
title: "No sound with flash player"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by Frebuche on 2009-11-02
Hello,

I recently made a fresh install of Kubuntu 9.10 64 bit.

I have sound for each applications except for the flash player in firefox and konkeror. All the channels of my Sound Blaster Audigy 2 ZS are unmuted in KMIX. 

I'm not used to solve sound problem with the phonon sound system. I was wondering if someone else is having this problem.

Thanx

---

### Post by allenkrell on 2009-11-09
I have the same problem.

---

### Post by ganjuror on 2009-11-22
same problem here too... seems to work sometimes if I quit amarok first, then restart ffox. sometimes needs a REBOOT! :(

---

### Post by fubofo on 2009-11-23
Hey guys I did the same. Fresh install of Kubuntu 64bit. Noticed that I had no sound in flash.

For some reason the PCM line of sound card is muted by default. Just change your audio settings in the mixer and it'll work......did for me!

---

### Post by rudie_techie on 2009-11-23
This is a bug with pulse audio. Have a look at this : [https://bugs.launchpad.net/ubuntu/+345096source/pulseaudio/+bug/](https://bugs.launchpad.net/ubuntu/+345096source/pulseaudio/+bug/). It seems that this was a bug with Kubuntu 9.04 64bit and is back in 9.10.

---

