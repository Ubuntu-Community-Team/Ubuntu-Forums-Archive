---
title: "ATI Driver failing on Jaunty"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by chicagofog on 2009-04-23
Here's what it does:
==================================================
ATI Technologies Linux Driver Installer/Packager
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.28-11-generic; make sure that the version is being
correctly set by --iscurrentdistro


-Any ideas?
Thanks

---

### Post by dot2kode on 2009-04-23
I'm having problems with video now also...I did an upgrade on my desktop/server (upgraded to jaunty server) and it does not play video's at all...Laptop has the Intel Graphics Media Accelerator 4500MHD  card in it and it play's but its choppy as hell with bad, bad tearing.  Trying to figure it out now.  If I find something I'll post back in here...In the mean time if anyone has any idea's please post. :confused:```

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
	Subsystem: Acer Incorporated [ALI] Device 015e
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
	Latency: 0
	Capabilities: [e0] Vendor Specific Information <?>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Acer Incorporated [ALI] Device 015e
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 2297
	Region 0: Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
	Region 2: Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Region 4: I/O ports at 1800 [size=8]
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
		Address: fee0300c  Data: 41b1
	Capabilities: [d0] Power Management version 3
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Acer Incorporated [ALI] Device 015e
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Region 0: Memory at f0400000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: [d0] Power Management version 3
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
[~] $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by sc0rp on 2009-04-24
> **chicagofog said:**
> Here's what it does:
==================================================
ATI Technologies Linux Driver Installer/Packager
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.28-11-generic; make sure that the version is being
correctly set by --iscurrentdistro


-Any ideas?
Thanks

Have you cleaned out the old drivers?
And downloaded the newest driver from ATI, should be 9.04.
I had a similar problem which was fixed by removing old ati driver and installing the new 9.04. I did a dist upgrade from Ubuntu 8.10 to Ubuntu 9.04 (amd64).

---

### Post by srigelsford on 2009-04-24
Use the new version (9.4) here:
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.9&lang=English&rev=9.4&ostype=Linux%20x86](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.9&lang=English&rev=9.4&ostype=Linux%20x86)


For some reason you can only find it if you search the ATI site, rather than going to drivers.

Sam.

---

### Post by mongolianfireoil on 2009-04-24
I've tried the 9.4 and the 9.3 after doing the upgrade. This is on a laptop with the ati 1400 series video. The 9.3 gives the error message shown in this thread, the 9.4 just acts like it loads ok but then freezes when it tries to load X.

---

### Post by jett on 2009-04-26
I have a Lenovo T60 with an ATI Mobility x1300 - having same problem with it installing but not working after a reboot.

---

### Post by uniden9 on 2009-04-26
Sorry but the ATI x1300 is no longer supported in Catalyst 9.4, and for Jaunty you have to have 9.4 to support X.org 1.6.


[http://wiki.cchtml.com/index.php/9.4](http://wiki.cchtml.com/index.php/9.4)


Justin

---

### Post by jett on 2009-04-26
it looks like no 3D acceleration for me then ...

---

### Post by mongolianfireoil on 2009-04-27
I tried with a completely fresh install. the 9.4 does not appear to support the x1400 ati video at all. 
 
the default driver ubuntu installs isn't bad though. My framerates in glxgears did drop but the color seems to be better on the lcd monitor. The current fps are about 1k to 1.5k fps which isn't bad for being a non-vendor driver.

---

