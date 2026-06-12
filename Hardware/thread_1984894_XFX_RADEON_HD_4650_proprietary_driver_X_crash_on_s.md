---
title: "XFX RADEON HD 4650 proprietary driver X crash on startup"
date: 2012-05-22
forum: Hardware
---

### Post by ra1p3 on 2012-05-22
Hi,

My graphics card is
XFX HD-465X-YPF2 RADEON HD 4650

Doing a fresh install of Ubuntu 12.04. All packages updated. Installing the propriatery driver through "Additional drivers" GUI.

Install seems to complete but after reboot I only get the console log in prompt instead of the graphical one.

I am not an expert with linux systems. I have tried following approaches (separately and in combination) following the instructions found on internet.
- install the proprietary driver manually by downloading from ATI
- making initial xorg.conf (aticonfig --initial)
- trying different xorg.conf configurations

There is a definitive error in the xorg.0.log:
Caught signal 4 (Illegal instruction). Server aborting

I am posting you related files resulted after following actions:
1) Install ubuntu 12.04
2) Update all packages. Reboot
3) Install propriatery drivers (from Additional drivers)
4) Reboot


No idea how to get the card working. Any help appreciated.

---

### Post by QIII on 2012-05-22
The graphical install generally works.  But for some reason, some people have problems installing via the Additional Drivers method.  See my signature for the way I do it.

---

### Post by ra1p3 on 2012-05-23
Following the instructions you mentioned did not help. Here is what I did:

- install fresh 12.04
- sudo apt-get update
- sudo apt-get upgrade
- sudo reboot
- sudo apt-get remove --purge fglrx*
- sudo apt-get install fglrx fglrx-amdcccle
- sudo aticonfig --initial
- sudo reboot
- fails to start the graphical login screen. only shows console login. Same error in the Xorg.0.log

Relevant files attached.

---

### Post by QIII on 2012-05-23
Can't look at your .gz files right now, so bear with me.

Does your motherboard have integrated graphics, particularly Intel, and can you disable the integrated graphics in your BIOS settings?

---

### Post by ra1p3 on 2012-05-26
Not sure if there is an integrated graphics chip. Likely not. And it is not Intel mother board. Could not find any option of disabling graphics from BIOS.

---

### Post by ridingdirty on 2012-08-18
Hey there!  I have a Radeon 4650 as well, but not an XFX.  I was able to install successfully from the additional drivers.  I just picked the driver that was not from post release updates.  However when I tried to play steam games such as Left for Dead 2 or tf2 I get really choppy results.  I was wondering if you ever resolved your issue and if you had any luck with steam games?

Thank you!

---

