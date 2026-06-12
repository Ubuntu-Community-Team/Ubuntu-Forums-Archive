---
title: "External drive not recognized"
date: 2014-09-21
forum: Hardware
---

### Post by kellyvotrenom on 2014-09-21
Spent some time Googling my problem and didn't find any applicable information.

I have a new external USB drive that I am trying to format with Gparted but Ubuntu does not see the drive.  All my other drives mount but this one does not show up anywhere.   In addition, I have an Epson scanner that is no longer working, it did  work when I was running 13.10; it may not be  a related issue.  However, I have connected both devices to my laptop that runs Windows; the scanner works and the drive is detected in disk management.  I have tried plugging it into various ports with the same results

Here are the outputs of various scans that were suggested from other posts.  I am running 14.04 LTS

    sudo fdisk -l
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007aac8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   976771071   488134657    5  Extended
/dev/sda3       976771072   976773119        1024   82  Linux swap / Solaris
/dev/sda5          501760   976771071   488134656   8e  Linux LVM

Disk /dev/mapper/xubuntu--vg-root: 497.7 GB, 497654169600 bytes
255 heads, 63 sectors/track, 60503 cylinders, total 971980800 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/xubuntu--vg-root doesn't contain a valid partition table

Disk /dev/mapper/xubuntu--vg-swap_1: 2143 MB, 2143289344 bytes
255 heads, 63 sectors/track, 260 cylinders, total 4186112 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


     ls /dev/ | grep sd
sda
sda1
sda2
sda3
sda5

     after plugging in drive:
sda
sda1
sda2
sda3
sda5
sdb

      lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 010: ID 0b38:0010 Gear Head 107-Key Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 033: ID 047d:1020 Kensington Expert Mouse Trackball
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

    after pluggin in drive:
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 006: ID 174c:55aa ASMedia Technology Inc. ASMedia 2105 SATA bridge
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 010: ID 0b38:0010 Gear Head 107-Key Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 033: ID 047d:1020 Kensington Expert Mouse Trackball
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Thanks for your help

Mark Springer
industrial arts

---

### Post by weatherman2 on 2014-09-21
Look at the tail of /var/log/syslog

and/or the end of the output of the shell command "dmesg."  Anything related to USB or the drive?  Check the logs first, then plug the drive in and look for changes.

---

### Post by kellyvotrenom on 2014-09-22
At the end of DMESG I found what I think relates to this new drive. As opposed to all the other USB devices there is this message:

Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK

Here is the tail of DMESG output:

[71470.169932] usb 2-4: new high-speed USB device number 8 using ehci-pci
[71470.303614] usb 2-4: New USB device found, idVendor=174c, idProduct=55aa
[71470.303627] usb 2-4: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[71470.303634] usb 2-4: Product: ASMT1051
[71470.303640] usb 2-4: Manufacturer: asmedia
[71470.303644] usb 2-4: SerialNumber: 123456789269
[71470.304061] usb-storage 2-4:1.0: USB Mass Storage device detected
[71470.304173] usb-storage 2-4:1.0: Quirks match for vid 174c pid 55aa: 400000
[71470.304226] scsi18 : usb-storage 2-4:1.0
[71471.303842] scsi 18:0:0:0: Direct-Access     WDC WD10 02FBYS-18W8B0    0    PQ: 0 ANSI: 6
[71471.304475] sd 18:0:0:0: Attached scsi generic sg2 type 0
[71471.305550] sd 18:0:0:0: [sdb] 0 512-byte logical blocks: (0 B/0 B)
[71471.307426] sd 18:0:0:0: [sdb] Write Protect is off
[71471.307432] sd 18:0:0:0: [sdb] Mode Sense: 43 00 00 00
[71471.308430] sd 18:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[71471.316415] sd 18:0:0:0: [sdb] Attached SCSI disk
[71477.073288] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:c0:4a:00:d0:db:8e:08:00 SRC=192.117.17.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[71483.210243] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:fb:00:e0:4c:b5:e6:bd:08:00 SRC=192.117.17.217 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[71602.145163] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:c0:4a:00:d0:db:8e:08:00 SRC=192.117.17.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[71605.922700] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:fb:00:e0:4c:b5:e6:bd:08:00 SRC=192.117.17.217 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[71649.099431] usb 2-4: USB disconnect, device number 8
[71649.100345] sd 18:0:0:0: [sdb] Synchronizing SCSI cache
[71649.100505] sd 18:0:0:0: [sdb]  
[71649.100516] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[71703.878690] usb 2-4: new high-speed USB device number 9 using ehci-pci
[71704.012242] usb 2-4: New USB device found, idVendor=174c, idProduct=55aa
[71704.012254] usb 2-4: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[71704.012261] usb 2-4: Product: ASMT1051
[71704.012267] usb 2-4: Manufacturer: asmedia
[71704.012272] usb 2-4: SerialNumber: 123456789269
[71704.012692] usb-storage 2-4:1.0: USB Mass Storage device detected
[71704.012846] usb-storage 2-4:1.0: Quirks match for vid 174c pid 55aa: 400000
[71704.012905] scsi19 : usb-storage 2-4:1.0
[71705.012601] scsi 19:0:0:0: Direct-Access     WDC WD10 02FBYS-18W8B0    0    PQ: 0 ANSI: 6
[71705.013213] sd 19:0:0:0: Attached scsi generic sg2 type 0
[71705.014308] sd 19:0:0:0: [sdb] 0 512-byte logical blocks: (0 B/0 B)
[71705.015476] sd 19:0:0:0: [sdb] Write Protect is off
[71705.015485] sd 19:0:0:0: [sdb] Mode Sense: 43 00 00 00
[71705.017817] sd 19:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[71705.021444] sd 19:0:0:0: [sdb] Attached SCSI disk
[71727.217033] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:c0:4a:00:d0:db:8e:08:00 SRC=192.117.17.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[71731.100822] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:fb:00:e0:4c:b5:e6:bd:08:00 SRC=192.117.17.217 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[71749.871258] systemd-hostnamed[23256]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[71769.133775] usb 2-4: USB disconnect, device number 9
[71769.134797] sd 19:0:0:0: [sdb] Synchronizing SCSI cache
[71769.134925] sd 19:0:0:0: [sdb]  
[71769.134933] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[71852.288933] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:c0:4a:00:d0:db:8e:08:00 SRC=192.117.17.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[71855.506371] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:fb:00:e0:4c:b5:e6:bd:08:00 SRC=192.117.17.217 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[71899.790604] usb 2-4: new high-speed USB device number 10 using ehci-pci
[71899.924237] usb 2-4: New USB device found, idVendor=174c, idProduct=55aa
[71899.924249] usb 2-4: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[71899.924256] usb 2-4: Product: ASMT1051
[71899.924262] usb 2-4: Manufacturer: asmedia
[71899.924267] usb 2-4: SerialNumber: 123456789269
[71899.924683] usb-storage 2-4:1.0: USB Mass Storage device detected
[71899.924818] usb-storage 2-4:1.0: Quirks match for vid 174c pid 55aa: 400000
[71899.924879] scsi20 : usb-storage 2-4:1.0
[71900.924594] scsi 20:0:0:0: Direct-Access     WDC WD10 02FBYS-18W8B0    0    PQ: 0 ANSI: 6
[71900.925237] sd 20:0:0:0: Attached scsi generic sg2 type 0
[71900.926310] sd 20:0:0:0: [sdb] 0 512-byte logical blocks: (0 B/0 B)
[71900.928105] sd 20:0:0:0: [sdb] Write Protect is off
[71900.928117] sd 20:0:0:0: [sdb] Mode Sense: 43 00 00 00
[71900.931806] sd 20:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[71900.936187] sd 20:0:0:0: [sdb] Attached SCSI disk
[71977.360788] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:c0:4a:00:d0:db:8e:08:00 SRC=192.117.17.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[71979.687814] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:fb:00:e0:4c:b5:e6:bd:08:00 SRC=192.117.17.217 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[72068.229775] usb 2-4: USB disconnect, device number 10
[72068.230579] sd 20:0:0:0: [sdb] Synchronizing SCSI cache
[72068.230717] sd 20:0:0:0: [sdb]  
[72068.230724] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[72092.464778] usb 2-4: new high-speed USB device number 11 using ehci-pci
[72092.598336] usb 2-4: New USB device found, idVendor=174c, idProduct=55aa
[72092.598347] usb 2-4: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[72092.598355] usb 2-4: Product: ASMT1051
[72092.598361] usb 2-4: Manufacturer: asmedia
[72092.598366] usb 2-4: SerialNumber: 123456789269
[72092.598798] usb-storage 2-4:1.0: USB Mass Storage device detected
[72092.598951] usb-storage 2-4:1.0: Quirks match for vid 174c pid 55aa: 400000
[72092.599011] scsi21 : usb-storage 2-4:1.0
[72093.598695] scsi 21:0:0:0: Direct-Access     WDC WD10 02FBYS-18W8B0    0    PQ: 0 ANSI: 6
[72093.599317] sd 21:0:0:0: Attached scsi generic sg2 type 0
[72093.600401] sd 21:0:0:0: [sdb] 0 512-byte logical blocks: (0 B/0 B)
[72093.601417] sd 21:0:0:0: [sdb] Write Protect is off
[72093.601426] sd 21:0:0:0: [sdb] Mode Sense: 43 00 00 00
[72093.602527] sd 21:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[72093.611772] sd 21:0:0:0: [sdb] Attached SCSI disk

---

