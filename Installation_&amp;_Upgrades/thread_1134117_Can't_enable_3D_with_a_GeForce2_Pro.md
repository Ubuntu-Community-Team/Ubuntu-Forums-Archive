---
title: "Can't enable 3D with a GeForce2 Pro"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by MyInstallationNeedsHelp on 2009-04-23
I installed Ubuntu 9.04 and found that unlike in 8.04, I was unable to enable 3D.  I tried using synaptic to install the NVidia driver that supports the GeForce2 series cards, but the driver would not load.  I tried the NVidia configuration program, which said:

You do not appear to be using the NVIDIA X Driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X Server.

nvidia-xconfig didn't exist on my system.  I installed it from Ubuntu's site.  It ran once, altered my xconfig file (later causing my xserver not to run at all), and then somehow vanished from my system!

So how exactly do I get 3D working on my system?

Thanks!

---

### Post by Brian_the_King on 2009-04-23
Every time I install video drivers on my laptop, I get a error messages and other claims that the installation didn't work, but when I restart the system everything is installed, activated, and working fine.

Try a reboot before getting into anything more complicated.

---

### Post by MyInstallationNeedsHelp on 2009-04-23
Long since rebooted.  No longer have a working X Server.

---

### Post by flOOi!ghenTM on 2009-04-26
No other suggestions whatsoever?

---

### Post by RedStickHam on 2009-04-26
I tried to get my Nvidia driver to load as well and it didn't work.  I found a suggestion for a previous version of Ubuntu to use Envyng, which I found with Synaptic.  I used that tool in terminal mode, rebooted, and the driver is there.

Good luck.

RedStickHam

---

