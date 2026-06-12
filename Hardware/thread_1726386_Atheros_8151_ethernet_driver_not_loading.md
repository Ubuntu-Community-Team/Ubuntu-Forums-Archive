---
title: "Atheros 8151 ethernet driver not loading"
date: 2011-04-11
forum: Hardware
---

### Post by plasm980 on 2011-04-11
Short version:

I bought a new machine with an Atheros 8151 LAN adapter on the motherboard.  After installing 10.10 64-bit, the ethernet doesn't work.  The driver module atl1e is already present in the distribution, but even running modprobe atl1e and depmod doesn't make it work.  What do I do?

Long version:

The motherboard is a ASRock H61M/U3S3 with on-board LAN.  According to the ASRock [website]("http://www.asrock.com/mb/overview.asp?Model=H61M/U3S3&cat=Specifications"), the LAN chip is an Atheros 8151.

I downloaded the driver source from the Atheros webpage [here]("http://partner.atheros.com/Drivers.aspx"), but was unable to compile it.  The error I get when running make is:
> Makefile:105: *** Linux kernel source not configured - missing autoconf.h.  Stop.
I have all the linux-headers packages installed as well as the linux-source-2.6.35 and build-essential.

I believe the module that should be built by the downloaded source is the atl1e module, which I discovered is actually already included in the 10.10 distribution at /lib/modules/2.6.35-22-generic/kernel/drivers/net/atl1e/atl1e.ko.

The Atheros ethernet controller appears on lshw as UNCLAIMED and lspci, but eth0 doesn't appear on ifconfig.  I tried running modprobe atl1e and depmod, but the adapter still isn't working, even after a reboot.  According to [this thread]("http://ubuntuforums.org/showthread.php?t=1476231"), it might have to do with different pci.id as my device is listed in lspci as [1969:1083] while modinfo atl1e contains strings with *1969*1066* and *1969*1026* in the alias fields (where * is a bunch of other characters).

How do I get my ethernet working?  Is 64-bit a problem?

Thanks!

---

### Post by leohart on 2011-04-22
Have you gotten more luck with this? I am having a rather new laptop running 10.10 which also has problems working with this Atheros Ethernet device.

---

### Post by Brouham on 2011-04-22
I had the same problem. Upgraded to ubuntu 11.04 beta and it worked because of included drivers in that distro. Ubuntu 11.04 final is due out next week.

---

### Post by Witt3439 on 2011-04-22
I had the same problem on my laptop that runs the exact same network card when trying to use 10.10 so I didn't expect much from 11.04 beta, but I was surprised with how fast 11.04 picked up my wired connection. It even switches from wireless to wired depending on whether I have an ethernet cable plugged in or not.

FWIW, I never did get my wired connection to work with 10.10.

---

### Post by tosh755 on 2011-06-16
Have you tried the solution given in "Networking & Wireless/Atheros AR8151 ethernet on Asus P8H67-V"?

---

