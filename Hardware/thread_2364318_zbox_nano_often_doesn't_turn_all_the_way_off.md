---
title: "zbox nano often doesn't turn all the way off"
date: 2017-06-21
forum: Hardware
---

### Post by edcompsci on 2017-06-21
Can't seem to get it to shut down all the way most of the time. It's kind of hit or miss, sometimes it shuts down all the way, other times is goes to a halted state and I have to push the button to turn it off. Both of these were fine for a while but now it seems to sometimes take several tries to turn it back on so it can actually finish shutting down before I can start it back up I have Ubuntu Studio dual booted with Centos on it. Otherwise the box works great.

The CPU is Intel Celeron N2930 quad core 2M Cache up to 2.16 GHz.
[http://ark.intel.com/products/81073/Intel-Celeron-Processor-N2930-2M-Cache-up-to-2_16-GHz](http://ark.intel.com/products/81073/Intel-Celeron-Processor-N2930-2M-Cache-up-to-2_16-GHz)

I tried using the alternate microcode cpu driver for Intel CPUs as well, 
I'll try to add some of the things I see on the screen next time it shuts halts but doesn't shut off.

I see someone else had a similar issue but I don't see the answere here:
[https://ubuntuforums.org/archive/index.php/t-1095887.html](https://ubuntuforums.org/archive/index.php/t-1095887.html)

Any help is appreciated. I'm going to try adding acpi=force (instead of the current setting of off)  and apm=Power_off to  GRUB_CMDLINE_LINUX_DEFAULT  then in etc/modules add apm power_off=1 and see if that works.
[https://ubuntuforums.org/showthread.php?t=2364318](https://ubuntuforums.org/showthread.php?t=2364318)
Also, if it halts but doesn't power off, it often takes many times turning on then off then on then off then on (etc.) before it will boot all the way into my logon screen, which fears me to think one day it won't turn on at all.  It is Ubuntu Studio but it dual boots to Centos.

---

### Post by edcompsci on 2017-06-29
in case anyone is interested, the few days after I did what I stated above, it still doesn't shut down all the way, but it seems to start back up without multiple tries.  I will continue to monitor this.

---

