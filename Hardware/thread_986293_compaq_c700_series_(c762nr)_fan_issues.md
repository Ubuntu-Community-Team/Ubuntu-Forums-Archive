---
title: "compaq c700 series (c762nr) fan issues"
date: 2008-11-18
forum: Hardware
---

### Post by busstation16 on 2008-11-18
I was having issues with my fans not coming till the computer was burning hot, then they would com on full blast for a minute, then tun off again.  Running acpi would show a temp of 0.  

Doing: 
sudo apt-get install lm-sensors
sudo sensors-detect

then I installed the sensor applet for the Panel and showing my CPUs.

After a restart (which it seems was infact necessary) All seems to be working.  I see the CPU temps just fine, and the fan it spinning away on low.

If anybody else has tried this, let me know if it or soemthing else helped.

---

### Post by dustin2929 on 2009-10-30
> **busstation16 said:**
> I was having issues with my fans not coming till the computer was burning hot, then they would com on full blast for a minute, then tun off again.  Running acpi would show a temp of 0.  

Doing: 
sudo apt-get install lm-sensors
sudo sensors-detect

then I installed the sensor applet for the Panel and showing my CPUs.

After a restart (which it seems was infact necessary) All seems to be working.  I see the CPU temps just fine, and the fan it spinning away on low.

If anybody else has tried this, let me know if it or soemthing else helped.

Yes I had the same problem on mine and this has fixed it as well. I've just installed ubuntu 9.10

---

### Post by JGrosman on 2011-03-19
The over heating problem is there is not enough air getting to the fan.   On the bottom of the computer where the fan is take a little  screwdriver and make some of the holes bigger.   It is a design flaw.   Once the holes are bigger everything will work with out overheating the  computer.   Try to solve the simple problems first.

---

