---
title: "Firmware bug when logging in to laptop with locked screensaver"
date: 2013-09-30
forum: Hardware
---

### Post by raubvogel on 2013-09-30
laptop in question is a Toshiba Satelite L640D. OS is ubuntu 13.04. Sometimes when I let it lock its screen (screensaver set to 3 minutes with password protection), when it comes back it will freeze on me with the 
```

[ 6562.038340] (Firmware Bug): cpu1: try to use APIC500 (LVT offset 0) for vector 0x400, but the register is already in use for vector 0xf9 on another cpu
```

message on the screen. Only way to get it working is rebooting (pressing and holding power buttom will do, which would make me think some stuff is working). Once I reboot I find nothing (or I am looking at the wrong stuff) in syslog or messages or dmesg or lastboot. 

I have not been able to isolate what causes that to happen: I might have no application running or  ton of them. Or be connected to a charger or running out of battery. Or laptop might have been sitting on my desk while I go get a drink of sleeping in my bag for a day.

Suggestions?

---

### Post by mörgæs on 2013-10-01
How does it work in a live boot of 13.10?

---

