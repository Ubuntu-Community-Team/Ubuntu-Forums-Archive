---
title: "lm-sensors fail on IBM Thinkcentre M51 w. Intel 82801FB ICH6"
date: 2010-03-28
forum: Hardware
---

### Post by mikrogroove on 2010-03-28
Been pulling what little hair I've got left on this for a couple days now. I've installed a second graphics card in my small form factor ThinkCentre M51 and am concerned about what impact this will have on temperatures. So, after reading a bit about system monitoring under Ubuntu I went ahead and installed lm-sensors and the sensors-applet. Unfortunately, running "sudo sensors-detect" fails to detect any sensors and ends with[INDENT]```
Do you want to probe the I2C/SMBus adapters now? (YES/no): 
Using driver `i2c-i801' for device 0000:00:1f.3: Intel 82801FB ICH6
Sorry, no sensors were detected.
```[/INDENT]I would have thought the Intel 82801FB ICH6 is a fairly standard chip and I'm surprised it doesn't work with lm-sensors. After all, IIRC this is the standard I/O Controller Hub for the i915G chipset. Am I missing some package here? I'm running Ubuntu Server 9.10 with kernel 2.6.31-14-generic-pae. 

Any help much appreciated! 

P.S. The second graphics card is an ATI HD 2400 Pro PCI and works well with the 2:8.660-0ubuntu4 fglrx drivers, fgl_glxgears gives me 750-800fps and fglrxinfo reports ATI Technologies Inc, ATI Radeon HD 2400, OpenGL version 2.1.9016. I have posted this question on the [Debian forums](http://forums.debian.net/viewtopic.php?f=5&t=50580) as well.

---

### Post by Mark Phelps on 2010-03-30
It is a fairly standard chip -- I have one on my tablet PC. And, like you, I've been unable to find a version of LM sensors that will detect and use the chip.

---

