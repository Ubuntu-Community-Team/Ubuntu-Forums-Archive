---
title: "No Plymouth Splash on SIS m760gx"
date: 2010-05-09
forum: Hardware
---

### Post by crazydahveed on 2010-05-09
I just upgraded to Lynx the other day and subsequently lost my boot splash (post Grub, pre login; aka Plymouth).  I have been looking around in desperation trying to locate a solution, but I have yet to find one that works.  I have tried:

echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash
update-initramfs -u

Although it lengthened my start-up time, I still had no splash screen.  I am assuming it has something to do with my Mirage 2 video card (integrated; part of SIS m760gx chipset).  Any thoughts?

I have no idea what to troubleshoot in order to determine exactly why the Plymouth splash screen is not appearing, so any thoughts would be appreciated.

---

### Post by mhgsys on 2010-05-11
I'm not sure if this works out for you , but it worked out for me on my sis 771/671.
To get a readable plymouth/ tty.. open up a terminal.
typ;
```
sudo bash
```

```
enter your password
```
(you'll be root)
typ;
```
echo blacklist vga16fb > /etc/modprobe.d/blacklist-vga16fb.conf
```

```
update-initramfs -u
```

followed by a reboot

```
reboot
```

---

### Post by crazydahveed on 2010-05-14
Unfortunately, that did not work.  To add a few more details, I do not get a splash screen at boot-up or shut down.  Most people I have talked with only have problems at boot-up due to the video drivers taking too long to load.  However, I am not getting the plymouth splash screen at shut down either.  I also cannot enable "Desktop Effects"/compiz.  But that doesn't surprise me much seeing as it is not much of a video card.

Video card details from lspci:
```
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
	Subsystem: Acer Incorporated [ALI] Device 0083
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 7
	BIST result: 00
	Region 0: Memory at e8000000 (32-bit, prefetchable) [size=128M]
	Region 1: Memory at e2100000 (32-bit, non-prefetchable) [size=128K]
	Region 2: I/O ports at a000 [size=128]
	Capabilities: [40] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] AGP version 3.0
		Status: RQ=256 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW- AGP3+ Rate=x4,x8
		Command: RQ=1 ArqSz=0 Cal=0 SBA- AGP- GART64- 64bit- FW- Rate=<none>
	Kernel modules: sisfb
```


I am also receiving an error message on start up (when plymouth should be displaying the splash screen).  I pulled it out of dmesg:
```
acer-wmi: No or unsupported WMI interface, unable to load
```

I am wondering if it is a video card driver issue.  Any thoughts?

---

### Post by mhgsys on 2010-05-15
[http://ubuntuforums.org/showthread.php?t=1471845](http://ubuntuforums.org/showthread.php?t=1471845)
(about the wmi problem)

---

### Post by crazydahveed on 2010-05-15
> **mhgsys said:**
> [http://ubuntuforums.org/showthread.php?t=1471845](http://ubuntuforums.org/showthread.php?t=1471845)
(about the wmi problem)

Unfortunately, that did not work.  From everything I read, that solution only applies to Intel integrated cards.  I have an SIS integrated card.  I am not willing to attempt the upstream kernel right now as I would lose my wireless drivers if I did that (per Ubuntu documentation).  Any other thoughts?  Thanks!

---

### Post by mhgsys on 2010-05-26
[https://bugs.launchpad.net/getdeb.net/+bug/584339](https://bugs.launchpad.net/getdeb.net/+bug/584339)

> installing v86d true synaptic does solve this problem;
however, adding sisfb to /etc/modules does just as well.

---

