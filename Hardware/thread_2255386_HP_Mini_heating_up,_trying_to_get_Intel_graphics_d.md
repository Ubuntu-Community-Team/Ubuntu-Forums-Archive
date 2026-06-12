---
title: "HP Mini heating up, trying to get Intel graphics drivers"
date: 2014-12-04
forum: Hardware
---

### Post by ryank76nz on 2014-12-04
I've installed Lubuntu on an HP Mini and it's fast and goes well. 

On bootup it heats up from 30 degrees to 60 degrees, which is uncomfortable and can't be good for it.

I tried the intel-linux-graphics-installer (latest version 1.0.7 from [https://01.org/linuxgraphics/downloads/2014/intelr-graphics-installer-linux-1.0.7](https://01.org/linuxgraphics/downloads/2014/intelr-graphics-installer-linux-1.0.7)) and it just says 'Distribution not supported'. 

This is my setup:
```
ryan@ryan-HP-Mini-110-3000:~$ lspci -k | grep -iA2 VGA
00:02.0 VGA compatible controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
	Subsystem: Hewlett-Packard Company Device 148a
	Kernel driver in use: i915

```

Is there a different kernel driver I should use? Or another way to reduce heat?

Thanks for any help

---

### Post by maxmuoto on 2014-12-04
> **ryank76nz said:**
> I've installed Lubuntu on an HP Mini and it's fast and goes well. 

On bootup it heats up from 30 degrees to 60 degrees, which is uncomfortable and can't be good for it.

I tried the intel-linux-graphics-installer (latest version 1.0.7 from [https://01.org/linuxgraphics/downloads/2014/intelr-graphics-installer-linux-1.0.7](https://01.org/linuxgraphics/downloads/2014/intelr-graphics-installer-linux-1.0.7)) and it just says 'Distribution not supported'. 

This is my setup:
```
ryan@ryan-HP-Mini-110-3000:~$ lspci -k | grep -iA2 VGA
00:02.0 VGA compatible controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
    Subsystem: Hewlett-Packard Company Device 148a
    Kernel driver in use: i915

```

Is there a different kernel driver I should use? Or another way to reduce heat?

Thanks for any help

The intel linux graphic installer does not support ubuntu 14.10 it only supports ubuntu 14.04.  To reduce heat maybe try installing a power management program like tlp.

To install tlp.

> sudo add-apt-repository ppa:linrunner/tlp

sudo apt-get update

sudo apt-get install tlp tlp-rdw

sudo tlp start

---

### Post by ryank76nz on 2014-12-06
Thank you, that's got it down to 53-54 degrees.

I guess I'll wait for Intel to catch up!

---

### Post by mörgæs on 2014-12-06
Did you check the fan and heatsink for dust?

---

