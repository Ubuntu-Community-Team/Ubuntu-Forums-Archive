---
title: "External hard drive does not show up"
date: 2017-10-18
forum: Hardware
---

### Post by olivercgrant on 2017-10-18
I've read a few forum posts and I think my hard drive is broken, but I'd like to know what I can do to test or confirm deadness.

It's a 3TB Western Digital MyBook HDD. It used to work on this computer and then stopped. Other hard drives can connect. I've broken it out of it's shell and put it in another working caddy, but get the same result. I also put a working harddrive into the WD caddy and it worked. So it's the harddrive. It still powers up and I can hear the spinning and "crunching of data" noise that normally happens before the folder window pops up. But the folder window doesn't pop up and the drive isn't showing up in /media/oliver 

Here's some potentially useful info that was requested in similar posts:

$ lsusb
Bus 002 Device 003: ID 5986:0400 Acer, Inc 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**Bus 004 Device 002: ID 1058:1130 Western Digital Technologies, Inc. My Book Essential (WDBACW)**
**Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub**
Bus 003 Device 003: ID 8087:07da Intel Corp. 
Bus 003 Device 002: ID 0c45:0520 Microdia MaxTrack Wireless Mouse
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



$ dmesg | tail -n 20
[ 2648.442384] usb 4-2: reset SuperSpeed USB device number 2 using xhci_hcd
[ 2648.458561] usb 4-2: LPM exit latency is zeroed, disabling LPM.
[ 2648.578387] usb 4-2: reset SuperSpeed USB device number 2 using xhci_hcd
[ 2648.594570] usb 4-2: LPM exit latency is zeroed, disabling LPM.
[ 2648.714378] usb 4-2: reset SuperSpeed USB device number 2 using xhci_hcd
[ 2648.730636] usb 4-2: LPM exit latency is zeroed, disabling LPM.
[ 2648.850574] usb 4-2: reset SuperSpeed USB device number 2 using xhci_hcd
[ 2648.866607] usb 4-2: LPM exit latency is zeroed, disabling LPM.
[ 2648.978406] usb 4-2: reset SuperSpeed USB device number 2 using xhci_hcd
[ 2648.994632] usb 4-2: LPM exit latency is zeroed, disabling LPM.
[ 2649.114560] usb 4-2: reset SuperSpeed USB device number 2 using xhci_hcd
[ 2649.130633] usb 4-2: LPM exit latency is zeroed, disabling LPM.
[ 2649.250441] usb 4-2: reset SuperSpeed USB device number 2 using xhci_hcd
[ 2649.266517] usb 4-2: LPM exit latency is zeroed, disabling LPM.
[ 2649.386583] usb 4-2: reset SuperSpeed USB device number 2 using xhci_hcd
[ 2649.402654] usb 4-2: LPM exit latency is zeroed, disabling LPM.
[ 2649.522566] usb 4-2: reset SuperSpeed USB device number 2 using xhci_hcd
[ 2649.538692] usb 4-2: LPM exit latency is zeroed, disabling LPM.
[ 2649.658667] usb 4-2: reset SuperSpeed USB device number 2 using xhci_hcd
[ 2649.674792] usb 4-2: LPM exit latency is zeroed, disabling LPM.


oliver@olytop:~/work$ sudo fdisk -l
[sudo] password for oliver: 
Disk /dev/loop0: 81,4 MiB, 85348352 bytes, 166696 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop1: 85 MiB, 89128960 bytes, 174080 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop2: 81,4 MiB, 85348352 bytes, 166696 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop3: 83 MiB, 87080960 bytes, 170080 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/sda: 477 GiB, 512110190592 bytes, 1000215216 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x98bd9ff3


Device     Boot     Start        End   Sectors   Size Id Type
/dev/sda1  *         2048     206847    204800   100M  7 HPFS/NTFS/exFAT
/dev/sda2          206848  262143999 261937152 124,9G  7 HPFS/NTFS/exFAT
/dev/sda3       262144000  359800249  97656250  46,6G 83 Linux
/dev/sda4       359800832 1000214527 640413696 305,4G 83 Linux

Please let me know if you have any ideas/suggestions or if I just need to give up on it. 
Assume I know nothing about hard drives, all the commands are copy pasta from other posts.
I know this isn't ubuntu specific, but I thought I'd try.

---

### Post by Autodave on 2017-10-18
Sounds like you need a new HD. The controller board has obviously failed.

---

### Post by olivercgrant on 2017-10-19
Thanks Autodave, that's useful to know.

I actually have another Western digital HD sitting here with the same controller board / PCB / circuit board (number starting 2061), that I'll try swapping onto the defective drive. I found a seller of these on ebay yesterday, that I can't find again today, who put a red circle around a small piece I needed to swap over from the faulty PCB. 

However, the donor drive is now too precious, so I'll have to wait for my replacements to arrive before attempting this.

---

