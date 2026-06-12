---
title: "Suspend and Hibernate Problems"
date: 2009-05-01
forum: Hardware
---

### Post by vhenry on 2009-05-01
Hi,

I'm a newly converted Ubuntu user. After trying Intrepid via Wubi on Vista, I made the jump and did a clean install of Jaunty. Besides a few quirks, one major problem.

When my HP dv9330 laptop went into hibernate, it didn't want to come back. The drive spun up, hard drive lights flashed, but screen remained dark. Ultimately had to reboot. 

At the least, I wonder if this constant rebooting will eventually corrupt the OS, and at worst, if I turn off hibernate/suspend, my laptop is running at full power -all day, everyday.

Any solutions?

---

### Post by jbrown96 on 2009-05-01
It's usually a problem with your graphics card or wireless. Could you post the output of the following
```
lspci
``` If you are using a NVidia/ATI graphics card, what drivers?

---

### Post by vhenry on 2009-05-01
> **jbrown96 said:**
> It's usually a problem with your graphics card or wireless. Could you post the output of the following
```
lspci
``` If you are using a NVidia/ATI graphics card, what drivers?

It looks like I hadn't selected a graphics driver. I do have an Nvidia card, and I went to: System, administration, hardware drivers and options are nvidia accelerated graphics driver 180 (recommended), 173 and 96. assuming I should activate the recommended one? 

lspci output:
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
05:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

---

### Post by jbrown96 on 2009-05-01
Activate the 180 driver and restart. Suspend worked for me after enabling the driver. 

It used to be required to make a few changes to some config files, but that's not necessary now. Having said that, after making the changes, my laptop resumes about twice as fast. I would recommend doing them; it only takes about 3 minutes.

[https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend]("https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend")

---

### Post by vhenry on 2009-05-01
> **jbrown96 said:**
> Activate the 180 driver and restart. Suspend worked for me after enabling the driver. 

It used to be required to make a few changes to some config files, but that's not necessary now. Having said that, after making the changes, my laptop resumes about twice as fast. I would recommend doing them; it only takes about 3 minutes.

[https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend]("https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend")

Worked like a charm, thanks!!

---

