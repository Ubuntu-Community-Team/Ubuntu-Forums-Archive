---
title: "LITE-ON LTR-52246S not detected by cdrecord"
date: 2006-07-09
forum: Hardware &amp; Laptops
---

### Post by armon_d on 2006-07-09
I am having trouble burning with my lite-on drive.
the outout of
```
dmesg | grep drive
```
is
[42949375.070000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[42949375.080000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[42949375.080000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[42949376.940000] hda: WDC WD100BB-75CLB0, ATA DISK drive
[42949377.240000] hdb: WDC WD1600JB-00GVA0, ATA DISK drive
[42949378.090000] hdc: Lite-On LTN486 48x Max, ATAPI CD/DVD-ROM drive
[42949378.570000] hdd: LITE-ON LTR-52246S, ATAPI CD/DVD-ROM drive
[42949378.750000] hdc: ATAPI 48X CD-ROM drive, 120kB Cache, UDMA(33)
[42949378.750000] Uniform CD-ROM driver Revision: 3.20
[42949378.760000] hdd: ATAPI 12X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[42949379.200000] usbcore: registered new driver usbfs
[42949379.200000] usbcore: registered new driver hub
[42949379.210000] USB Universal Host Controller Interface driver v2.3
[42949385.980000] Floppy drive(s): fd0 is 1.44M
[42949386.530000] Initializing USB Mass Storage driver...
[42949386.530000] usbcore: registered new driver usb-storage
[42949386.650000] cx2388x v4l2 driver version 0.0.5 loaded
[42949386.860000] usbcore: registered new driver hiddev
[42949387.110000] usbcore: registered new driver usbhid
[42949387.110000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[42949388.130000] lp0: using parport0 (interrupt-driven).
[42949388.790000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[42949391.610000] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[42949392.270000] IPv6 over IPv4 tunneling driver
[42949404.090000] tun: Universal TUN/TAP device driver, 1.6

/dev/hdd is the drive in question.
```
dmesg | grep hdd
```
shows 
[42949376.630000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:pio
[42949378.570000] hdd: LITE-ON LTR-52246S, ATAPI CD/DVD-ROM drive
[42949378.760000] hdd: ATAPI 12X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[42949399.280000] cdrom: hdd: mrw address space DMA selected
[42950986.610000] hdd: command error: status=0x51 { DriveReady SeekComplete Error }
[42950986.610000] hdd: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[42950986.610000] end_request: I/O error, dev hdd, sector 0
[42950986.610000] Buffer I/O error on device hdd, logical block 0
[42950986.690000] hdd: command error: status=0x51 { DriveReady SeekComplete Error }
[42950986.690000] hdd: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[42950986.690000] end_request: I/O error, dev hdd, sector 0
[42950986.690000] Buffer I/O error on device hdd, logical block 0.

The result of ```
cdrecord -scanbus
``` shows the following
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.15-25-server
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
Linux sg driver version: 3.5.33
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
Using libscg version 'debian-0.8debian2'.
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
scsibus0:
        0,0,0     0) 'PLEXTOR ' 'DVDR   PX-712A  ' '1.07' Removable CD-ROM
        0,1,0     1) *
        0,2,0     2) *
        0,3,0     3) *
        0,4,0     4) *
        0,5,0     5) *
        0,6,0     6) *
        0,7,0     7) *

Thanks for any help! I realize that I already have a burner, but I cannot enable DMA on it, so burning at 2x is a real drag.

---

### Post by armon_d on 2006-07-10
Never mind! I fixed the problem. I just edited /etc/cdrecord/cdrecord and made the default device /dev/hdd even though it wasn't detected by cdrecord -scanbus. This way I can still use the ridiculously slow burner and my lovely fast 52x burner!

---

