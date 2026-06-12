---
title: "Lenovo y430 sound problem"
date: 2009-02-22
forum: Hardware
---

### Post by Upas on 2009-02-22
Hey guys, I'm dual booting Ubuntu 8.10 on my Lenovo Y430. Everything works great so far except for this one aspect.

The Lenovo Y430 comes with a Dolby Digital "subwoofer" on the bottom of the computer. Now this subwoofer works fine when I'm playing music through my speakers, but when I put headphones in, the normal speakers shut off as they are supposed to, but the subwoofer does not.

The result is I have sound coming through my headphones, and a muffled  bass-only sound coming from my laptop. Since I work in public spaces a lot, this will not do. I need to be able to silence my laptop completely with headphones, not just make it less noisy.

Are there any drivers available to fix this, or any other fixes I could use?

---

### Post by Upas on 2009-04-14
Necro bump. I still have this problem.

---

### Post by Miroku on 2009-05-03
any success with 9.04 if u upgraded?

---

### Post by abitom on 2009-05-15
Installed 9.04 had the same trouble.... :mad:

---

### Post by njd4k on 2009-05-15
If you right-click on the volume icon, you can bring up a sound manager that on my machine has access to multiple different sound drivers. (So when an upgrade shifted all the balance to my right speaker, I fiddled with all the balance options until I found the left speaker all the way down in one panel.)

If you open the manager, do you see any options for the subwoofer?

---

### Post by cheatex on 2009-05-31
Hi,
ii have same problem...
> **njd4k said:**
> If you open the manager, do you see any options for the subwoofer?
No, there is no any options for subvoofer.

---

### Post by cheatex on 2009-06-01
I found simple solution: reboot to windows, plug headphones and boot back to linux ;)

---

### Post by crash187 on 2009-09-03
has anyone found a better fix for this i really am considering going all ubuntu

---

### Post by shortcut144 on 2009-09-10
No, I've been searching forever.  I'm hoping that that the new 2.6.31 kernel helps.  This sound issue is a major pain for me.

I've gone all Linux and I'm... OK with it... I guess.  I'm pushing through and hoping I can find a fix for the Lenovo Y430 sound issue... some day.

---

### Post by mientefuego on 2009-10-29
It seems that upgrading to 9.10 solves the problem.

As a matter of fact, I did not upgrade, I installed Karmic Koala from scratch. If you don't get that by simply upgrading the system, you may try that.

---

### Post by tonyshangrila on 2009-11-04
> **mientefuego said:**
> It seems that upgrading to 9.10 solves the problem.

As a matter of fact, I did not upgrade, I installed Karmic Koala from scratch. If you don't get that by simply upgrading the system, you may try that.

I tried installing 9.10 from scratch on my Y430, was not as lucky. :(

---

### Post by Nixikanius on 2009-11-12
> **tonyshangrila said:**
> I tried installing 9.10 from scratch on my Y430, was not as lucky. :(

I have same problem on 9.10. Rebooting throught Windows helps, but it isn't a good idea to solve problem...

---

### Post by Nixikanius on 2009-12-06
Hey, guys!

Did anybody solve this problem?

---

### Post by jmzcray on 2010-05-20
me too, just recently installed 10.04

the headphones does not mute the speaker. I have tried ALL combination to put in the /etc/modprobe.d/alsa-base.conf for the line 

snd-hda-intel model=xxx

aplay -l gives:
> card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

head -n 1 /proc/asound/card0/codec* gives:
> ==> /proc/asound/card0/codec#0 <==
Codec: Intel G45 DEVCTG

==> /proc/asound/card0/codec#2 <==
Codec: Conexant CX20561 (Hermosa)

---

### Post by jmzcray on 2010-05-23
More info for the bump -->

lsb_release -rd gives:
------------------------------------------------------
Description:	Ubuntu 10.04 LTS
Release:	10.04
-----------------------------------------------------

I have tried to update the alsa-driver to 1.0.23 by following this website:
                 [http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)
however, after a reboot, the alsa-driver seems to revert back to 1.0.22.1 (see below)

uname -a gives:
-----------------------------------------------------
Linux lynxY430 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux
-----------------------------------------

cat /proc/asound/version gives:
---------------------------------------------------------------
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Apr 29 2010 for kernel 2.6.32-22-generic (SMP).
---------------------------------------------------------------

I have also register it as a bug here:
[https://bugs.launchpad.net/ubuntu/+bug/583292](https://bugs.launchpad.net/ubuntu/+bug/583292)

if this problem affects you, please click on:
[https://bugs.launchpad.net/ubuntu/+bug/583292/+affectsmetoo](https://bugs.launchpad.net/ubuntu/+bug/583292/+affectsmetoo)

Thanks!

---

