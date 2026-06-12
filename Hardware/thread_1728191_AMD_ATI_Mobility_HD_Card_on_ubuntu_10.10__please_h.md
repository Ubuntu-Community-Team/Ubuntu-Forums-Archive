---
title: "AMD ATI Mobility HD Card on ubuntu 10.10  please help"
date: 2011-04-13
forum: Hardware
---

### Post by adel.sartawi on 2011-04-13
using lspci

> 00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
01:00.1 Audio device: ATI Technologies Inc RV710/730
02:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)


using glxgears 

> Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
302 frames in 5.0 seconds = 60.356 FPS
301 frames in 5.0 seconds = 60.107 FPS
301 frames in 5.0 seconds = 60.107 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 2302 requests (2301 known processed) with 0 events remaining.

and using glxinfo | grep direct
> direct rendering: Yes


low frame rate why ?](*,)

---

### Post by Yellow Pasque on 2011-04-13
because your refresh rate is 60Hz...
> Running synchronized to the vertical refresh. The framerate should be
approximately the same as the monitor refresh rate.
... hence the 60fps.

glxgears is not a benchmark!](*,)

---

### Post by adel.sartawi on 2011-04-13
upppppppppppppppppppppppppppppppp

---

### Post by Yellow Pasque on 2011-04-13
> **adel.sartawi said:**
> upppppppppppppppppppppppppppppppp
You bumped in 3 minutes? Don't do that.

---

### Post by adel.sartawi on 2011-04-13
> **Temüjin said:**
> because your refresh rate is 60Hz...

... hence the 60fps.

glxgears is not a benchmark!](*,)

so is that ok ?

---

### Post by adel.sartawi on 2011-04-13
can't enable the desktop effects and customisation please help !

---

### Post by Yellow Pasque on 2011-04-13
> **adel.sartawi said:**
> so is that ok ?
Yes.

---

### Post by adel.sartawi on 2011-04-13
```
$lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]

$ compiz
compiz (core) - Error: Couldn't load plugin 'ccp'
Couldn't find a perfect decorator match; trying all decorators
Found no decorator to start
compiz (core) - Error: Couldn't load plugin 'ccp'
Couldn't find a perfect decorator match; trying all decorators
```

---

### Post by adel.sartawi on 2011-04-13
```
$lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]

$ compiz
compiz (core) - Error: Couldn't load plugin 'ccp'
Couldn't find a perfect decorator match; trying all decorators
Found no decorator to start
compiz (core) - Error: Couldn't load plugin 'ccp'
Couldn't find a perfect decorator match; trying all decorators
```

help please enable the desktop effects Just for learning

---

### Post by howefield on 2011-04-13
Threads merged.

Please have some patience. Bump once after 24(ish) hours have passed with no reply.

---

