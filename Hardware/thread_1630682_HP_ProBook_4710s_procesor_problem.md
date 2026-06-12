---
title: "HP ProBook 4710s procesor problem"
date: 2010-11-25
forum: Hardware
---

### Post by Tom4z on 2010-11-25
Hello there! 

I am new to linux and i have a problem that i hope you will help me solving it. 


Here is what im using :
- HP ProBook 4710s
- Ubuntu 10.10 i386

Now the problem is that it doesnt detects my second cpu, it only detects one cpu. That causes my procesor to run all the time on maximum performance and the laptop is heating! 
I tried with installing cpufrequtils but it doesnt helps. I also installed all updates and the problem is still not solved. 

Can you please help me? Im depending on you guys!


P.S. Sorry for my grammar if i maked some mistakes

---

### Post by Fafler on 2010-11-26
You only have one CPU, but it have two cores. It's very unlikely that the kernel only detects one of the cores. Open a terminal and:

```
cat /proc/cpuinfo | grep name

```

If you only get one line, you're right and probably have a serious BIOS/ACPI/APIC problem. If it gives you two lines, it already uses both cores and your problem is somewhere else.

Try running top and look for any threads that use a lot of processing power. And make sure you've installed the 3rd. party ATI driver for your Radeon. The default open source driver have some powersaving issues and makes the chip run quite hot, even when doing nothing.

---

### Post by Tom4z on 2010-11-26
Hello!

Well i installed the driver for my graphic card (mobility radeon) and it solved mi problem! Now everything runs just fine!

Thanks for the help!

Problem solved

---

