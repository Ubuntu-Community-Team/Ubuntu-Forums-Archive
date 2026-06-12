---
title: "Intel HD graphics and Ubuntu version"
date: 2014-03-31
forum: Hardware
---

### Post by cyb0rgb0rg on 2014-03-31
Hi.

I am a returning user after a few years absence. My question is back at the newbie stage. I wonder which version of the OS to use this time. I am very old school and I would like to run Compiz with cube and all the bells and whistles like in the good old days. Last time I set up Ubuntu I was on a backported 10.04 on an Alienware m14x using the Intel graphics only using the glazen mesa stuff.

This time I'm on a Dell Latitude E5530 with the following setup. I have tried just about anything to get the desktop effects going but no luck. I pulled out some old tricks, and after reading up a bit I installed some newer kernels. It just won't budge. :( I hope somebody can help me, because I am no fan of Unity or any of the new stuff.

lspci:
```

00:00.0 Host bridge: Intel Corporation Device 0154 (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Device 0166 (rev 09)
00:14.0 USB Controller: Intel Corporation Device 1e31 (rev 04)
00:16.0 Communication controller: Intel Corporation Device 1e3a (rev 04)
00:1a.0 USB Controller: Intel Corporation Device 1e2d (rev 04)
00:1b.0 Audio device: Intel Corporation Device 1e20 (rev 04)
00:1c.0 PCI bridge: Intel Corporation Device 1e10 (rev c4)
00:1c.1 PCI bridge: Intel Corporation Device 1e12 (rev c4)
00:1c.2 PCI bridge: Intel Corporation Device 1e14 (rev c4)
00:1c.3 PCI bridge: Intel Corporation Device 1e16 (rev c4)
00:1c.5 PCI bridge: Intel Corporation Device 1e1a (rev c4)
00:1c.6 PCI bridge: Intel Corporation Device 1e1c (rev c4)
00:1d.0 USB Controller: Intel Corporation Device 1e26 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Device 1e57 (rev 04)
00:1f.2 RAID bus controller: Intel Corporation Mobile 82801 SATA RAID Controller (rev 04)
00:1f.3 SMBus: Intel Corporation Device 1e22 (rev 04)
02:00.0 Network controller: Intel Corporation WiFi Link 6000 Series (rev 35)
0b:00.0 SD Host controller: O2 Micro, Inc. Device 8221 (rev 05)
0c:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5761 Gigabit Ethernet PCIe (rev 10)

```

lscpu:
```
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
CPU(s):                4
Thread(s) per core:    2
Core(s) per socket:    2
CPU socket(s):         1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 58
Stepping:              9
CPU MHz:               1200.000
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              4096K

```

less /proc/cpuinfo excerpt:
```
model name      : Intel(R) Core(TM) i7-3540M CPU @ 3.00GHz
```

uname -r
```
3.9.0-030900-generic
```

glxgears
```
Unrecognized deviceID 0x166
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  27
  Current serial number in output stream:  29

```

Thanks in advance to anyone who can school this poor soul. :)

Carl

---

### Post by trag on 2014-03-31
I recommend Zorin 12.04 LTS, very nice Win 7 like interface with some of the bells n' whistles already enabled with ability to enable more if you desire.

---

### Post by cyb0rgb0rg on 2014-03-31
> **trag said:**
> I recommend Zorin 12.04 LTS, very nice Win 7 like interface with some of the bells n' whistles already enabled with ability to enable more if you desire.

Thanks trag!

But I found a much better solution as Windows interface is not what I was after. I love the old skool gnomeish stuff. And it was right there. Xubuntu 13.10 with compiz!! :D:D:D

After some minor, and I mean minor, tweaking (no driver hassle, no backporting or other half good configs) I got my cube going with all the superduper snacks and my very gnomy desktop back! The ONLY thing I got working last time, which failed now, was the 3D windows while rotating. But I see that I could downgrade to the Natty compiz version for that. But I think I'll just leave it. It's super sweet as it is now.

All running on the fresh 8Gb i7 Dell laptop with Corsair Force ssd. Lightning quick and honkydory like grandma's butt on a barstool!!

Oh, the happiness!! The joy of making something work after a few hours of struggle.

C

---

