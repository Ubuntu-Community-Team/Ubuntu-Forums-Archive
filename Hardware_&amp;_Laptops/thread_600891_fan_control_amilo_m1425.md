---
title: "fan control amilo m1425"
date: 2007-11-02
forum: Hardware &amp; Laptops
---

### Post by lizardking on 2007-11-02
Hello,
I have got a amilo m 1425. I have some strange problem wih Acpi and fan control. The cpu freq. scaling is working but the fan speedstep does not work. I have a horrible noise by the cooler.
I have found a lots of web site that reports that like [this]("http://www.ailis.de/~k/archives/6-Linux-on-Fujitsu-Siemens-M1425.html").
Also in this site it reports some strange problem with acpi.
I noticed then following (quoting that site):
> 
Another interesting note: Gabor Keresztfalvi has disassembled the DSDT of the Amilo and found out that the thermal zones are hardcoded. That means its absolutely ok that linux says the CPU is 75°C hot. This temperature is hard coded to tell the operating system that everything is fine. If a critical event occurs then the temperature will be raised to a value greater then the hardcoded alarm temperature (85°C) to tell the operating system that something is fishy. 


Is strange that acpi have got always the CPU tmp like 75°C and the fan is not presente by proc in /proc/acpi/fan like report some website in /proc/acpi/fan/FAN like this [http://ubuntuforums.org/showthread.php?t=2122](http://ubuntuforums.org/showthread.php?t=2122)

They could set the fan speed editing that value that I haven't.

Someone could help me? I heard about editing the DSTD file of ACPI and compile it and put in the kernel to make some progress. But I'm unable to following this guide.

[http://laptopsurf.blogspot.com/2006/07/cpu-fan-control-problem-solved-amilo.html](http://laptopsurf.blogspot.com/2006/07/cpu-fan-control-problem-solved-amilo.html)

Some one could help me to write my DSTD? Should I fill a bug in launchpad?


Regards,

---

### Post by lizardking on 2007-11-02
**This post could be related to an Ubuntu bug filed at**: [https://bugs.edge.launchpad.net/ubuntu/+source/acpi/+bug/57617](https://bugs.edge.launchpad.net/ubuntu/+source/acpi/+bug/57617) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				The bug is well documentated here....

---

### Post by adrien214 on 2008-02-14
I answered your post on amilo-forum.com

I guess you should by now  either have figure out a solution, given up or realized there was no fan control ability in the ACPI...  :(

---

### Post by lizardking on 2008-02-14
> **adrien214 said:**
> I answered your post on amilo-forum.com

I guess you should by now  either have figure out a solution, given up or realized there was no fan control ability in the ACPI...  :(

I answered your post on amilo-forum.com too. I did not resolve anything. :mad:
let me know....

---

### Post by adrien214 on 2008-03-18
okay...
I have figured out a way to partially solve my fan speed problem - I simply elevated my laptop (I'll put a pic), this enables better air circulation, and so the fan doesn't blow as fast as it used to and the system temps are "relatively" low...
This isn't what I was expecting but it works fine :KS

---

