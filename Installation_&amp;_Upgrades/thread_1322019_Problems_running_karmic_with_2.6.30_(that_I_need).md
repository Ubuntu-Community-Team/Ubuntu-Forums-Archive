---
title: "Problems running karmic with 2.6.30 (that I need)"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by melenanyma on 2009-11-10
Karmic looks nice and I really like the way mythtv 0.22 adds new functionality to mythbuntu. Unfortunately I need to run karmic on the 2.6.30 kernel. A software tool I use will not work on 2.6.31.

So I tried by downloading the most recent 2.6.30.x provided for jaunty. It boots, and I get the onboard Nvidia graphics working without pain. 

Many devices however do not get added into their correct dev structure. The DVB card for instance can be found as: 
/dev/dvb0.demux0
/dev/dvb0.dvr0
/dev/dvb0.net0
/dev/dvb0.frontend0

whereas it should be in /dev/dvb/adapter0/dvr0 and similar for the others. I have moved the devices to apropriate places and yes that indeed gives me access to the devices using mythtv. It should however happen automatically.

Adding and modifying udev rules does not help as the system does not seem to respond to those. 

I really need to run on 2.6.30 So I home someone can soon help me out on this issue.

---

### Post by zingo on 2009-11-11
I get the same flat /dev filestructure when I also use 2.6.30 on 9.10 I can see that a alot of devices (all?) are flat in /dev not just /dev/dvb/* devices. I also don't get any audio but that could be the same problem, with the messed up /dev directory. Could there be some sort of udev problem (if it is udev that should create the links?)

---

### Post by zingo on 2009-11-13
Could there be some dependancy in devicekit/udev compared to hal that get broken when using 2.6.30 instead of 2.6.31?

---

### Post by melenanyma on 2009-11-14
You seem to have the exact same problem. If find that when I manually link or move the devs tot the right location, they simply work. Udev has certain rules for doing this during boot but they don't seem to get the right info from this kernel. I ve trid to make my own rules but there is no response whatsoever

This really bugging me as it holding me up in building a system for intensive use.

---

### Post by zingo on 2009-11-14
I wonder if there is some new stuff in the devicekit migration that also need to be backed out or reconfigured for 2.6.30 again. Do you also miss sound?

---

### Post by jarlethorsen on 2009-11-14
I also have the same problem as the original poster. If I can't get this working soon I'll guess I just have to backup and downgrade :( Hope somebody figures this out SOON!

---

### Post by Hammi on 2009-11-16
Have you tried this: [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/460388](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/460388)

Adding a udev rule worked for me. I tried, however, this one:

```
KERNEL=="dvb*", PROGRAM="/bin/sh -c 'K=%k; K=$${K#dvb}; printf dvb/adapter%%i/%%s $${K%%%%.*} $${K#*.}", ACTION=="add|change", NAME="%c"
SUBSYSTEM=="dvb", ACTION="add", GROUP="video"
```

Put it under some name in /etc/udev/rules.d

Despite the doc, it only worked for me after a reboot.

---

### Post by lordjoe on 2009-11-16
To fix missing DRI and alsa devices on older kernels, I took some other lines from the debian unstable udev package and put them in /etc/udev/rules.d/50-old-kernel-workaround.rules:

```

# DRI
KERNEL=="card[0-9]*", NAME="dri/%k"

# ALSA devices
KERNEL=="controlC[0-9]*", NAME="snd/%k"
KERNEL=="hwC[D0-9]*",   NAME="snd/%k"
KERNEL=="pcmC[D0-9cp]*",  NAME="snd/%k"
KERNEL=="midiC[D0-9]*",   NAME="snd/%k"
KERNEL=="timer",    NAME="snd/%k"
KERNEL=="seq",      NAME="snd/%k"

```

---

### Post by jarlethorsen on 2009-11-16
This worked for me: [http://ubuntuforums.org/showpost.php?p=8329657&postcount=6](http://ubuntuforums.org/showpost.php?p=8329657&postcount=6)

---

