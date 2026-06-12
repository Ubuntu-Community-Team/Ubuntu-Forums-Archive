---
title: "New Desktop , AMD, testing Ubuntu 64, black screen. AMDFM2 A10"
date: 2014-03-28
forum: Hardware
---

### Post by jackson21 on 2014-03-28
Hi, All, Have a brand new Desktop PC, Asrock FM2A55M-HD, AMD55 Socket FM2+,
AMDFM2+A10-7700K. 4x3.40Ghz, with integrated Radeon system
When testing the new hardware with Ubuntu 13.10 AMD 64 , I was rewarded with a  blank dark screen

So I am waiting for Ubuntu 14.04, 64MB  final release and hope for the best,

Thank you for reading this

jackson

---

### Post by Bashing-om on 2014-03-28
jackson21; Hi !

You do not specify the graphics in use:
> 
with integrated Radeon system

If this is 
a) dual graphics, maybe the system is confused and needs a bit of direction as to how to deal with the graphics card(s).
b) bleeding edge graphics card, such that linux has not caught up with the required driver, will have to, again, intervene manually.

In order to boot, one "may" be able to employ a boot parameter to direct the system to use the on-board graphics driver (llvmpipe)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) <- How to set NOMODESET and other kernel boot options in grub2

Once you are booting up, we can address the issue for a permanent solution.

[INDENT]where there are solutions
[INDENT][INDENT]there are no problems
[/INDENT][/INDENT][/INDENT]

---

### Post by jackson21 on 2014-03-29
Thank you Bashing-OM,   for suggestions,

The New Desktop-PC  has no graphics card,   radeon is integrated on motherboard!!

---

### Post by QIII on 2014-03-29
Actually, the CPU and GPU are on the same die on the A10, and the arrangement is called an APU for AMD products.  

You'lll need to boot with the nomodeset option as suggested and either set nomodeset permanently or install the proprietary AMD fglrx driver before you reboot.

I'd go for the proprietary driver, so have a look at the resource bashing-om provided.

Best wishes.

---

### Post by leonmaxx on 2014-03-29
Graphics chip is not on motherboard, but integrated into CPU. Kaveri CPUs are new so it's not surprise that they are not supported by Ubuntu 13.10.
There is a [final beta of Ubuntu 14.04]("http://releases.ubuntu.com/trusty/"), You could try use it.

---

### Post by jackson21 on 2014-03-29
Hi, leonmax, will try to install the final beta for Ubuntu 14.04,
Will keep you posted,

Thank you from jackson

---

### Post by jackson21 on 2014-03-29
Thank you, ubuntu 14.04  is running !

---

### Post by jackson21 on 2014-03-29
Thank you all, ubuntu was set up with nomodeset, 14,04 is beautiful

---

### Post by mörgæs on 2014-03-30
Good, please mark the thread 'solved'.

---

