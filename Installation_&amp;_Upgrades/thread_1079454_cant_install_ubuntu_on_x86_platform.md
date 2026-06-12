---
title: "cant install ubuntu on x86 platform"
date: 2009-02-24
forum: Installation &amp; Upgrades
---

### Post by sachin10190 on 2009-02-24
hi!!! geeks
i hv tried installing ubuntu(diff. versions),several times on my pc,installation completes successfully,but ubuntu dont start at all,dont even show progress bar,i think it has smthng to do wth my hardware

here is my system information:-

OS Name	Microsoft Windows XP Professional
Version	5.1.2600 Service Pack 3 Build 2600
OS Manufacturer	Microsoft Corporation
System Name	JAT
System Manufacturer	INTEL_
System Model	D845GVS1
System Type	X86-based PC
Processor	x86 Family 15 Model 4 Stepping 1 GenuineIntel ~2401 Mhz
BIOS Version/Date	Intel Corp. VA84510A.86A.0030.P10.0402160229, 2/16/2004
SMBIOS Version	2.3
Windows Directory	C:\WINDOWS
System Directory	C:\WINDOWS\system32
Boot Device	\Device\HarddiskVolume1
Locale	United States
Hardware Abstraction Layer	Version = "5.1.2600.5512 (xpsp.080413-2111)"


plz guys help me out!!!

---

### Post by Pumalite on 2009-02-24
Boot your Live CD and from the Terminal post:
```
sudo fdisk -lu
```

---

