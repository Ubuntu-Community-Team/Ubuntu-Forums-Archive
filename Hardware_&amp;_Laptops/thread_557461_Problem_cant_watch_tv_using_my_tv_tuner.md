---
title: "Problem: cant watch tv using my tv tuner"
date: 2007-09-22
forum: Hardware &amp; Laptops
---

### Post by elias85 on 2007-09-22
lspci gives:

$ lspci
00:00.0 Host bridge: ALi Corporation M1689 K8 Northbridge [Super K8 Single Chip]
00:01.0 PCI bridge: ALi Corporation AGP8X Controller
00:02.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge
00:03.0 ISA bridge: ALi Corporation M1563 HyperTransport South Bridge (rev 70)
00:03.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:04.0 Multimedia audio controller: ALi Corporation M5455 PCI AC-Link Controller Audio Device (rev 20)
00:0d.0 Ethernet controller: ALi Corporation ULi 1689,1573 integrated ethernet. (rev 40)
00:0e.0 IDE interface: ALi Corporation M5229 IDE (rev c7)
00:0f.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0f.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0f.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0f.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:07.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
---------------------------------------------------
i tried sudo modprobe cx88_dvb
and got:
FATAL: Error inserting cx88_dvb (/lib/modules/2.6.20-15-generic/kernel/drivers/media/video/cx88/cx88-dvb.ko): No such device

i tried: sudo modprobe xc88xx and it was ok
i tryied:
tvtime-scanner --input=0
and i got:
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/elias85/.tvtime/tvtime.xml
Scanning using TV standard PAL.
/home/elias85/.tvtime/stationlist.xml: No existing PAL station list "Custom".
videoinput: Can't get tuner info: Invalid argument
videoinput: Can't get tuner info: Invalid argument

No tuner found on input 0. If you have a tuner, please
select a different input using --input=<num>.

anyone to help me?

---

### Post by geraldm on 2007-09-23
Any hints in /var/log/dmesg ?
anything on the man page for your access program, like how to setup a configuration?

Gerald

---

### Post by stoodleysnow on 2007-09-23
I need a decent analog tv capture program that does not take over the whole computer. I:popcorn:deas?

---

### Post by w4ett on 2007-09-24
> **stoodleysnow said:**
> I need a decent analog tv capture program that does not take over the whole computer. I:popcorn:deas?

Try tvtime...it's available in Synaptic.

---

### Post by stoodleysnow on 2007-09-24
I've tried that, but it can't seem to tune in to UK Analog TV frequencies. It just goes straight past the TV channels, and anyway I need something I can copy videos to DVDs with, not just watch TV.

---

