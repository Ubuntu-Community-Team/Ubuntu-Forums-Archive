---
title: "Setting up LIRC for DViCO FusionHDTV7 Dual Express?"
date: 2009-04-09
forum: Hardware
---

### Post by daveisfera on 2009-04-09
I'm trying to get my remote working with Mythbuntu 9.04, but I haven't been able to find any sort of instructions on how to get it setup with my DViCO FusionHDTV7 Dual Expres.

I tried following [these instructions](http://www.mythtv.org/docs/mythtv-HOWTO.html#toc8.3), but when I run "irrecord", I get the following error:

```
irrecord -  application for recording IR-codes for usage with lirc

Copyright (C) 1998,1999 Christoph Bartelmus(lirc@bartelmus.de)

irrecord: could not get file information for /dev/lirc
irrecord: default_init(): No such file or directory
irrecord: could not init hardware (lircd running ? --> close it, check permissions)
```

I then stumbled along [this post](http://ubuntuforums.org/showthread.php?t=891270&page=2) and after running "sudo modprobe ir-kbd-i2c" I am able to get some of the key presses in irw (just the arrow keys and numeric keys).

So, then I tried placing the [DViCO lircd.conf file](http://lirc.sourceforge.net/remotes/dvico/lircd.conf.fusionHDTV) at /etc/lircd.conf and /etc/lirc/lircd.conf, but I still can only get the arrow keys and numeric keys in irw.


I noticed that the following device now appears in /proc/bus/input/devices:

```
I: Bus=0018 Vendor=0000 Product=0000 Version=0000
N: Name="i2c IR (FusionHDTV)"
P: Phys=i2c-0/0-006b/ir0
S: Sysfs=/devices/virtual/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: EV=100003
B: KEY=c00a4 230305100000000 0 110000 1b844002841 1e168000000000 10000ffc
```

I also noticed that the following lines are added to the dmesg output:

```
[  353.985785] input: i2c IR (FusionHDTV) as /devices/virtual/input/input7
[  354.012563] ir-kbd-i2c: i2c IR (FusionHDTV) detected at
i2c-0/0-006b/ir0 [cx23885[0]]
```

So my questions are:
what do I need to do to get the remote working all the time?
what do I need to do to get all of the buttons to be recognized?

Thanks,
Dave

---

### Post by onehotcutey on 2009-06-11
See Post 16 on this thread:

[http://ubuntuforums.org/showthread.php?t=891270&page=2](http://ubuntuforums.org/showthread.php?t=891270&page=2)

---

