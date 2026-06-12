---
title: "Kernel Problems"
date: 2009-10-02
forum: Installation &amp; Upgrades
---

### Post by zetanuxi on 2009-10-02
I have installed Ubuntu Studio because it is the only prepackaged version of Ubuntu that supports my wireless card on install (rt73). 

I've had to install the OS several times due to kernel panic. When I'm installing software and making upgrades, everything freezes up. I moved away from Windows to avoid this.

Could this be happening because of the rt kernel? Should I compile a standard kernel to use instead? (Not using Ubuntu Studio for any type of audio/video production).

Thanks in advance.

---

### Post by tommcd on 2009-10-02
The driver for the rt73 (as well as most of the other Ralink wireless cards) has been in the kernel for some time. This is not something unique to Ubuntu Studio. The drivers are present in Ubuntu Jaunty 9.04, as well as previous versions of the *buntu family:
[http://packages.ubuntu.com/jaunty/rt73-common](http://packages.ubuntu.com/jaunty/rt73-common)
[http://packages.ubuntu.com/jaunty/rt73-source](http://packages.ubuntu.com/jaunty/rt73-source)
I use the rt61 on a pcmcia wireless card on my laptop and every recent distro detects it automatically with no problem.

---

### Post by zetanuxi on 2009-10-02
So would it work the same to have the source files and the dependencies on a thumb drive, then install? My wireless card is the only way i can access my Internet.

Everywhere I look tells me that I need ndiswrapper for my wlan card. Is this true with the sources, or do the sources act as native drivers?

---

### Post by tommcd on 2009-10-03
> **zetanuxi said:**
> So would it work the same to have the source files and the dependencies on a thumb drive, then install? My wireless card is the only way i can access my Internet.
You should already have the driver. Run **lsmod** in the terminal and look for it. Are you able to boot into Ubuntu Studio to check this? 
> **zetanuxi said:**
> 
Everywhere I look tells me that I need ndiswrapper for my wlan card. Is this true with the sources, or do the sources act as native drivers?
The driver in the kernel is the native linux driver. This should work better than ndiswrapper.

---

