---
title: "USB data stick loses detection"
date: 2013-02-05
forum: Hardware
---

### Post by dolo724 on 2013-02-05
I recently installed Xubuntu 12.04 on an older machine, and it runs quite well except for an unexpected quirk. 

First, I insert a USB data stick, formatted vfat, and it automounts. It reads/writes no problem. I unmount the stick using the GUI button in Thunar in preparation to install a live o/s. I try to find it with gparted and fdisk, but the inserted USB stick does not appear. 

uname -a
```
Linux robbie 3.2.0-37-generic #58-Ubuntu SMP Thu Jan 24 15:28:57 UTC 2013 i686 i686 i386 GNU/Linux
```

Logs:
mount of USB data stick
```
[432.060049] usb 1-2: new high-speed USB device number 6 using ehci_hcd
[432.208171] scsi3 : usb-storage 1-2:1.0
[433.208843] scsi 3:0:0:0: Direct-Access Kingston DT 101 II 1.00 PQ: 0 ANSI: 2
[433.215146] sd 3:0:0:0: Attached scsi generic sg2 type 0
[433.217179] sd 3:0:0:0: [sdb] 7827456 512-byte logical blocks: (4.00 GB/3.73 GiB)
[433.218111] sd 3:0:0:0: [sdb] Write Protect is off
[433.218119] sd 3:0:0:0: [sdb] Mode Sense: 23 00 00 00
[433.220452] sd 3:0:0:0: [sdb] No Caching mode page present
[433.220461] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[433.223454] sd 3:0:0:0: [sdb] No Caching mode page present
[433.223463] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[433.332440]  sdb: sdb1
[433.336936] sd 3:0:0:0: [sdb] No Caching mode page present
[433.336944] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[433.336950] sd 3:0:0:0: [sdb] Attached SCSI removable disk
```

from fdisk -l:
```
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003e4cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   154693631    77345792   83  Linux
/dev/sda2       154695678   156248063      776193    5  Extended
/dev/sda5       154695680   156248063      776192   82  Linux swap / Solaris

Disk /dev/sdb: 4007 MB, 4007657472 bytes
61 heads, 21 sectors/track, 6110 cylinders, total 7827456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00059324

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1     7827455     3913727+  83  Linux

```

umount /media/Kingston:
```
[830.001445] sdb: detected capacity change from 4007657472 to 0
```

fdisk -l:
```
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003e4cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   154693631    77345792   83  Linux
/dev/sda2       154695678   156248063      776193    5  Extended
/dev/sda5       154695680   156248063      776192   82  Linux swap / Solaris
```

/dev/sdbX is missing!
finally, log on removal:
```
[1027.835100] usb 1-2: USB disconnect, device number 6
```

I'm perplexed. Is it hardware or software? I do have a newer machine to use, but IMHO this ain't right! 

Oh, btw, here's lspci:
```
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)
01:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:0e.0 FireWire (IEEE 1394): LSI Corporation FW322/323 (rev 61)

```yes, it's sharing RAM for video.

and lsusb, during mount and even after umount:
```
mike@robbie:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 001 Device 007: ID 0951:1625 Kingston Technology DataTraveler 101 II

```

Thanks in advance.

---

