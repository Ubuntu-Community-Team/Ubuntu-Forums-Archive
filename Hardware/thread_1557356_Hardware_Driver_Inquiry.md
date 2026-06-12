---
title: "Hardware Driver Inquiry"
date: 2010-08-20
forum: Hardware
---

### Post by tr1sth3t on 2010-08-20
I use an ATI Radeon X1650 Pro. In Ubuntu 8.04, I was notified that I could install restricted drivers for this hardware. I am now using Ubuntu 10.04, and anything with detailed graphic effects (games, compiz, etc.) lags. Are there any solutions for Ubuntu 10.04? Are there any accelerated drivers I can use?

UPDATE: I have downloaded the ATI driver for my hardware series. I installed and received the following output with errors. 

```

$ ./ati-driver-installer-9-3-x86.x86_64.run 
Created directory fglrx-install.gIFUAh
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.593...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.32-24-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.gIFUAh

```

SOME EXTRA INFORMATION:
```

$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon X1650 Pro (rev 9e)
01:00.1 Display controller: ATI Technologies Inc Radeon X1650 Pro (Secondary) (rev 9e)
02:01.0 Modem: Broadcom Corporation BCM4212 v.90 56k modem (rev 02)
02:02.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
02:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)

```

---

### Post by realzippy on 2010-08-20
The 9.3 catalyst is incompatible since 9.04...ATI dropped support for newer X version for "old" cards.You might use the free driver...

---

### Post by tr1sth3t on 2010-08-20
> **realzippy said:**
> The 9.3 catalyst is incompatible since 9.04...ATI dropped support for newer X version for "old" cards.You might use the free driver...
can you tell me the name of the free driver, and where to get it?

---

### Post by realzippy on 2010-08-21
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)


should help you.If you want the best 3D acceleration,the combination
Old Ubuntu+9.3 might be superior to New Ubuntu+Free driver...

---

