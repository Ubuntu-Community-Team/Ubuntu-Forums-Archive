---
title: "Nvidia Drivers Problems"
date: 2009-01-14
forum: Hardware
---

### Post by Stieffers on 2009-01-14
I've been having issues getting the non-open source Nvidia drivers working.  Every time I active the proprietary drivers and restart Xserver, I get stuck in a command line.  At this point, I'm forced to replaced my xorg.conf file with xorg.conf.failsafe, and then restart KDE. 

I checked for any errors being thrown and found that Xserver was reporting that the necessary power connection to my video card was not made.  I double checked this, and the video card is plugged directly into the PSU, as directed.

I'm assuming the issue is that once the drivers are installed, the new config file is trying to set the monitor/GFX card to an unsupported mode.  Hence, Xserver is unable to initiate.  Even if this is the problem, I'm unsure how to correct it.  Any help is much appreciated.

**System Specs**:
AMD Athlon XP 2100+
1GB DDR Ram
Nvidia Geforce FX 5900
40 GB HD (ext3)
120 GB HD (ntfs)

**Edit**:

Issue solved.  My graphics card was reporting that the necessary power supply connection was not made, even though it was.  Adding...

```
Option "NoPowerConnectorCheck" "true"
```

...right before the end of the "Screen" section in my xorg.conf file solved the problem.

---

