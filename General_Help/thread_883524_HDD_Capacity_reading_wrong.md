---
title: "HDD Capacity reading wrong?"
date: 2008-08-08
forum: General Help
---

### Post by terry123b99 on 2008-08-08
Hi Guys,

Strange problem here, I have a laptop with 250GB hard drive (not in any RAID configuration) and Ubuntu says I have a 450GB hard drive.

Can anyone shine any light on this?

BTW am running 8.04

Cheers

Terry

---

### Post by forger on 2008-08-08
hm.. usually the disk space is limited :D You've probably stumbled upon a bug of some sort
Is the disk ATA or SATA? Or is it USB?
Did you install Ubuntu from windows (using wubi)?
Or if you used the live cd, was it the same in live CD?

Open Applications > Accessories > Terminal, maximize the window and run these commands:
```
ls -l /dev/disk/by-id
lspci
lsusb

```

Post back with the output :)

---

### Post by terry123b99 on 2008-08-08
The disk is an internal laptop SATA drive as far as am aware, here is the info you requested.
> 
terry@terry-laptop:~$ ls -l /dev/disk/by-id
total 0
lrwxrwxrwx 1 root root  9 2008-08-08 05:25 ata-WDC_WD2500BEVS-22UST0_WD-WXCZ07549865 -> ../../sda
lrwxrwxrwx 1 root root 10 2008-08-08 05:25 ata-WDC_WD2500BEVS-22UST0_WD-WXCZ07549865-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-08-08 05:25 ata-WDC_WD2500BEVS-22UST0_WD-WXCZ07549865-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2008-08-08 05:25 ata-WDC_WD2500BEVS-22UST0_WD-WXCZ07549865-part5 -> ../../sda5
lrwxrwxrwx 1 root root  9 2008-08-08 05:25 scsi-1ATA_WDC_WD2500BEVS-22UST0_WD-WXCZ07549865 -> ../../sda
lrwxrwxrwx 1 root root 10 2008-08-08 05:25 scsi-1ATA_WDC_WD2500BEVS-22UST0_WD-WXCZ07549865-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-08-08 05:25 scsi-1ATA_WDC_WD2500BEVS-22UST0_WD-WXCZ07549865-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2008-08-08 05:25 scsi-1ATA_WDC_WD2500BEVS-22UST0_WD-WXCZ07549865-part5 -> ../../sda5
terry@terry-laptop:~$ 


> 
terry@terry-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GS (rev a1)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
0a:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
0a:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0a:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
0a:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
0a:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
terry@terry-laptop:~$ 


> 
terry@terry-laptop:~$ lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 064e:a101 Suyin Corp. 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
terry@terry-laptop:~$ 


---

### Post by terry123b99 on 2008-08-08
also forgot to mention, installed from live cd and was the same in there :)

---

### Post by forger on 2008-08-10
can you post the output of this command too:
```
sudo df -h
```

---

