---
title: "Ubuntu boots into blank screen"
date: 2010-12-22
forum: Hardware
---

### Post by zealkaiser on 2010-12-22
Whenever I try to boot Ubuntu Live CD it shows a blank screen. This happens with all the linux distros that i have tried including ubuntu 10.4, 9.10, kubuntu 10.04, fedora 13, opensuse 11.1, puppy 5, puppy 4, knoppix

The only way to run ubuntu is using boot options
i915.modeset=0 xforcevesa

Since my laptop has a 15.6inch screen 1024x768 resolution in vesa mode looks too much ugly.

I have reported a bug at [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/693273](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/693273)

---

### Post by theasprint on 2010-12-22
Hi,

So can i know your graphics card model? 

If unsure about the model, once booted in Ubuntu, go to terminal and type
```
lspci | grep VGA
```

And what do you want to do? 
Do you want to install Ubuntu? 
Because there should be a fix when you decided to install Ubuntu.

---

### Post by Fafler on 2010-12-22
From the bug report:
```
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
	Subsystem: Mitac Device [1071:9525]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 2299
	Region 0: Memory at c0000000 (64-bit, non-prefetchable) [size=4M]
	Region 2: Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Region 4: I/O ports at 1800 [size=8]
	Capabilities: <access denied>

00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
	Subsystem: Mitac Device [1071:9525]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Region 0: Memory at f8100000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

```
Try this (man i'm lazy today): [www.google.com/search?q=Intel+Corporation+Mobile+4+Series+Chipset+Integrated+Graphics+Controller+ubuntu](www.google.com/search?q=Intel+Corporation+Mobile+4+Series+Chipset+Integrated+Graphics+Controller+ubuntu)

You could also take a look at what happens when you get the blank screen. Let it boot up from the CD and press ctrl+alt+f1. Hopefully, you should get a text login. Google for the default username and password for your live system, login and take a look at your log file:
```
less /var/log/Xorg.0.log
```
(WW) are warnings and (EE) are errors.

---

### Post by zealkaiser on 2010-12-27
Thanks guys for taking interest in my problem.

First of all i cannot start the ubuntu at all without i915.modeset=0.
So firstly i want to know what does that mean.

Secondly, if I start with i915.modeset=0 boot option the ubuntu loads normally but as soon as loading completes or you can say when it enters xorg, ubuntu freezes. Screen becomes black. So at that point how can i take the log of Xorg.

Currently, i have installed Slitaz 3.0
It does not freezes but it was not also going beyond 800x600 resolution. But after installing xf86-video-intel, libdrm, mesa, mesa-dri and mesa-dri-intel in slitaz I can get 1360x768 resolution and there is no problem regarding graphics although performance is not that awesome related to graphics.
May be that can help to figure out the problem

---

