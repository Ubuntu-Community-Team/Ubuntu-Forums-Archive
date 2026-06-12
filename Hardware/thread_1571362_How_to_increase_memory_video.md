---
title: "How to increase memory video?"
date: 2010-09-09
forum: Hardware
---

### Post by samigina on 2010-09-09
Hi, Im using Ubuntu 10.04


lspci -v


00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
	Subsystem: Lenovo Device 3870
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f0500000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 1800 [size=8]
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Memory at f0600000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

So, my video chip is capable to take 256mb and...


dmesg | grep agpgart


[    1.592799] Linux agpgart interface v0.103
[    1.620277] agpgart-intel 0000:00:00.0: Intel 945GME Chipset
[    1.620617] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[    1.624478] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000

....is taking just 8mb, no matter if I try to run a game, it stays in 8mb, so no good games can be run.

Theres a manual way to fix the size of the video memory?

Oh and my bios doesnt have an option for that.

---

### Post by Yellow Pasque on 2010-09-09
I think you're reading it wrong. It is at 256MB.

---

### Post by Fafler on 2010-09-09
The aparture size doesn't really have anything to do with the available amount of graphics memory. [http://www.techpowerup.com/articles/overclocking/vidcard/43](http://www.techpowerup.com/articles/overclocking/vidcard/43)

From the intel driver manpage:

```
       The  Intel  8xx and 9xx families of integrated graphics chipsets have a
       unified memory architecture meaning that system memory is used as video
       RAM.   For  the i810 and i815 family of chipsets, operating system sup&#8208;
       port for allocating system memory is required  in  order  to  use  this
       driver.   For  the  830M  and  later, this is required in order for the
       driver to use more video RAM than has been pre-allocated at  boot  time
       by  the BIOS.  This is usually achieved with an "agpgart" or "agp" ker&#8208;
       nel driver.  Linux, FreeBSD, OpenBSD, NetBSD,  and  Solaris  have  such
       kernel drivers available.

       By  default,  the i810/i815 will use 8 MB of system memory for graphics
       if AGP allocable memory is < 128 MB, 16 MB if < 192  MB  or  24  MB  if
       higher. Use the VideoRam option to change the default value.

       For  the  830M and later, the driver will automatically size its memory
       allocation according to the features it will support.   Therefore,  the
       VideoRam  option,  which  in  the past had been necessary to allow more
       than some small amount of memory to be allocated, is now ignored.

```

Still, 8 mb doesn't seem like much. How much main memory do you have? I think GMA950 should go up to 256 mb.

---

### Post by IcarusR on 2010-09-09
I have same grafix card & get same results from both commands. Runs well, but do not play games. Can watch HD video no problem.

What games are you playing & how, natively or under wine ?? Some games do not work well with wine.

---

### Post by Yellow Pasque on 2010-09-09
> Still, 8 mb doesn't seem like much. How much main memory do you have? I think GMA950 should go up to 256 mb.
I don't see 8MB reported anywhere. I see the following, but it is normal and doesn't indicate the amount of video RAM:
```
detected 7932K stolen memory
```

/var/log/Xorg.0.log might be more specific.

---

