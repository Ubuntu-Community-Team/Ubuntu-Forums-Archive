---
title: "ATI Mobility Radeon 3600 based on which chipset"
date: 2009-09-13
forum: Hardware
---

### Post by jivan28 on 2009-09-13
Hi all, 
  Noob here. I just got a Dell xps 1640 and it says it has the following card when I look it up via lspci. 

```
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility HD 3670
```

while the graphics card is working and I can use the proprietary flgrx driver (if I want) I want to know on which chipset its based. 

I got some info. on the community drivers KMS stuff happening on [http://kernelnewbies.org/LinuxChanges](http://kernelnewbies.org/LinuxChanges)

> 1.4. ATI Radeon Kernel Mode Setting support
This version adds Kernel Mode Setting (KMS) support for ATI Radeon. Hardware supported is R1XX,R2XX,R3XX,R4XX,R5XX (radeon up to X1950). Works is underway to provide support for R6XX, R7XX and newer hardware (radeon from HD2XXX to HD4XXX).

The kernel version given is 2.6.31

---

### Post by ShirishAg75 on 2009-09-13
LOL, its the R600 chipset. Coincidentally (or not) I just put up a blog post on the same family of chipsets at [http://flossexperiences.wordpress.com/2009/09/13/dell-xps-16/](http://flossexperiences.wordpress.com/2009/09/13/dell-xps-16/)

---

