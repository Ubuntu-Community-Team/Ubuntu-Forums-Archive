---
title: "DKMS Synaptics Drivers?"
date: 2013-01-11
forum: Hardware
---

### Post by hamberglar on 2013-01-11
I have an Avatar Mercury Ultrabook. It's a not-so-well-known company located in LA that I suspect has their computers assembled in China. My laptop is, well to be honest, a blatant MacBook Air knock off. Nearly identical dimensions and specs to the 13" Macbook air. I digress.

This particular laptop comes equipped with an PS/2 Elantech Touchpad (lifted from xinput list).

It has multigesture support for 2 finger scrolling, but it doesn't work with ubuntu out of the box. Bugfix pages suggest I install the synaptics-dkms driver. Through much searching and updating and hopeless terminal work... I finally got it installed through a .deb package.

The touchpad help page suggests I then reboot, open mouse settings and go to the touchpad tab to change gestures and other settings.

But... that doesn't exist. The mouse and touchpad settings in 12.10 haven't changed since I installed ubuntu and don't contain any of the settings I'm looking for (just settings revolving around double clicking and whatnot).

Does anyone have any suggestions? I'd really like to get scrolling working and be able to disable the touchpad while I'm typing (the pad is in an unfortunate position, so my palm hits it while I'm typing).

I'm not entirely attached to 12.10 if changing ubuntu versions would help.

Disclaimer: I'm a bit of an ubuntu noob and don't really know what I'm doing.

---

### Post by Nevetsjc on 2013-01-12
Have you had a look through [https://wiki.ubuntu.com/Multitouch](https://wiki.ubuntu.com/Multitouch) ?
That suggests using Ginn (should be in the software center), or else try this howto with Touchegg: [http://www.howtogeek.com/howto/43097/how-to-get-macbook-style-finger-gestures-on-ubuntu-linux/](http://www.howtogeek.com/howto/43097/how-to-get-macbook-style-finger-gestures-on-ubuntu-linux/)

---

### Post by numb3rlady on 2013-08-02
I have tried every dkms module possible: elantech v6, elantech v7, and alps. I have also tried 4 distros: arch, opensuse, fedora, and ubuntu, and no fix. Its really aggravating because I love this machine, but I'll have to get rid of it if I can't get this fixed. Sometimes the cursor/arrow jumps to the left every 30 seconds or so and I have to restart it. Also, upon wakeup, it will shutdown after about 30 seconds. The chipset is HM77 intel i5-3317u, and the hardware is confirmed as elantech v6. HELP.

---

### Post by matt29 on 2013-09-10
Were you able to resolve this problem?  I recently decided to try to install ubuntu 12.04 on my laptop (avatar mercury / aviu) and have the same problem.  Every second the mouse jumps a few inches left and registers a click. Were you able to find a version of ubuntu that didn't have this problem?

---

