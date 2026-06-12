---
title: "Toshiba Satellite WiFi driver ... what do these errors mean?"
date: 2010-01-23
forum: Hardware
---

### Post by SkankinRatFink on 2010-01-23
Hello everyone.

What I'm trying to do is get the wireless internet working on a Toshiba Satellite L505-S5988 laptop. The WiFi device is a Realtek 8172.

I downloaded the driver, rtl8192se_linux_2.6.0010.1012.2009.tar.gz. I installed the package "build-essential." When I decompressed the archive, I ran the following commands:

**make** - worked fine, no errors.

**sudo make install** - produced errors.

[INDENT]make[3]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[2]: *** [prepare0] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-17-generic-pae'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/mehdi/Downloads/rtl8192se_linux_2.6.0010.1012.2009/HAL/rtl8192'
make: *** [install] Error 2[/INDENT]

I don't really know what to make of these. Please help.

---

### Post by amandkumar on 2010-01-23
Even i am having the same laptop facing the same problem.  I went to toshiba site and installed the driver for wifi den it worked out. Try downloading the softwares from the company site not from some where else.

---

### Post by rogue_0111 on 2010-01-23
--

Try this thread:

[http://ubuntuforums.org/showthread.php?t=1328209](http://ubuntuforums.org/showthread.php?t=1328209)

--

---

