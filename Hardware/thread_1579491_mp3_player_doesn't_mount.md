---
title: "mp3 player doesn't mount"
date: 2010-09-21
forum: Hardware
---

### Post by jfca283 on 2010-09-21
hi
the mp3 player, fujitel 2gb, is detected, but isn't mounted
what can i do?
```
sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006baf3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4379    35172353    5  Extended
/dev/sda3            4380       19457   121114035   83  Linux
/dev/sda5               1        4262    34231296   83  Linux
/dev/sda6            4262        4379      940032   82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xffaeffae

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24321   195358401   83  Linux

Disk /dev/sdc: 2130 MB, 2130141696 bytes
66 heads, 62 sectors/track, 1016 cylinders
Units = cylinders of 4092 * 512 = 2095104 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System

```

```
juan@juan-desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 005: ID 10d6:1101 Actions Semiconductor Co., Ltd D-Wave 2GB MP4 Player / AK1025 MP3/MP4 Player
Bus 004 Device 002: ID 04f3:0230 Elan Microelectronics Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
is this a kernel bug?...this is the first time i've had a problem with a generic mp3 player
thanks for your help and interest

---

### Post by tangchengguang on 2010-09-22
Firstly,detect the file format of your mp3 player. It could be NTFS or FAT32. Run the following commands in your terminal:
**$cat /proc/partitions**
Check what the partition label of your mp3 player is.
Assume it's file format FAT32 and it's partition label is **sdc**1.
And then you can run:
[B]$sudo mkdir -p /media/mp3
$sudo mount -t vfat /dev/sdc1 /media/mp3
Scd /media/mp3
$ls -alh[/B]
Now,it's OK.

---

### Post by jfca283 on 2010-09-22
this i what i get
```
juan@juan-desktop:~$ cat /proc/partitions
major minor  #blocks  name

   8        0  195360984 sda
   8        1  195358401 sda1
   8       16  156290904 sdb
   8       17          1 sdb1
   8       19  121114035 sdb3
   8       21   34231296 sdb5
   8       22     940032 sdb6
   8       32    2080216 sdc

```
no sdc1, just sdc...
i did
sudo mount -t vfat /dev/sdc /media/Mp3
but mounting it takes long time, and i can't write on it for some permission issues
however, on windowsXP i can write and use it normally
is this a bug?
look what i get if i type...
```
juan@juan-desktop:~$ dmesg | grep usb
[    0.276354] usbcore: registered new interface driver usbfs
[    0.276381] usbcore: registered new interface driver hub
[    0.276435] usbcore: registered new device driver usb
[    0.461496] usb usb1: configuration #1 chosen from 1 choice
[    0.462145] usb usb2: configuration #1 chosen from 1 choice
[    0.462587] usb usb3: configuration #1 chosen from 1 choice
[    0.463021] usb usb4: configuration #1 chosen from 1 choice
[    0.463454] usb usb5: configuration #1 chosen from 1 choice
[    0.957288] usb 4-2: new low speed USB device using uhci_hcd and address 2
[    1.130109] usb 4-2: configuration #1 chosen from 1 choice
[    1.763059] usbcore: registered new interface driver hiddev
[    1.776421] input: USB+PS/2 Optical Mouse as /devices/pci0000:00/0000:00:10.2/usb4/4-2/4-2:1.0/input/input5
[    1.776648] generic-usb 0003:04F3:0230.0001: input,hidraw0: USB HID v1.11 Mouse [USB+PS/2 Optical Mouse] on usb-0000:00:10.2-2/input0
[    1.776696] usbcore: registered new interface driver usbhid
[    1.776703] usbhid: v2.6:USB HID core driver
[   91.656044] usb 1-5: new high speed USB device using ehci_hcd and address 3
[   91.801921] usb 1-5: configuration #1 chosen from 1 choice
[   91.893060] usbcore: registered new interface driver usb-storage
[   91.894693] usb-storage: device found at 3
[   91.894698] usb-storage: waiting for device to settle before scanning
[   96.892265] usb-storage: device scan complete
[  127.928054] usb 1-5: USB disconnect, address 3
[  128.360023] usb 4-1: new full speed USB device using uhci_hcd and address 3
[  128.515270] usb 4-1: not running at top speed; connect to a high speed hub
[  128.542424] usb 4-1: configuration #1 chosen from 1 choice
[  128.550038] usb-storage: device found at 3
[  128.550044] usb-storage: waiting for device to settle before scanning
[  133.549432] usb-storage: device scan complete
[  163.932547] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[  194.928035] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[  225.928030] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[  256.928039] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[  287.940044] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[  318.224076] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[  349.112137] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[  380.116054] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[  411.112036] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[  442.113998] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[  473.112036] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[  504.112078] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[  535.112057] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[  566.112036] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[  597.120080] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[  628.112045] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[  659.112040] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[  690.112038] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[  721.112042] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[  752.112053] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[  783.112034] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[  814.112040] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[  845.112040] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[  876.112067] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[  907.112066] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[  938.112069] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[  969.112069] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[ 1000.112032] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[ 1031.112033] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[ 1062.112049] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[ 1093.112037] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[ 1124.112084] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[ 1155.112055] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[ 1186.116060] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[ 1217.112028] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[ 1248.112035] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[ 1279.112036] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[ 1310.112542] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[ 1341.116033] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[ 1372.116123] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[ 1403.112047] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[ 1434.112938] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[ 1465.116047] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[ 1496.112051] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[ 1527.112046] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[ 1558.116125] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[ 1589.112041] usb 4-1: reset full speed USB device using uhci_hcd and address 3
[ 1620.118217] usb 4-1: reset full speed USB device using uhci_hcd and address 3
```
if i mount it like root, i can see it from nautilus, but i can't permissions or i can't even unmount it like root
it's a kernel bug?

why my Pendrive is detected by 
**sudo fsck -l** like /dev/sdc and not /dev/sdc1?
gparted can't handle it...any suggestion?

---

### Post by flosn on 2011-10-13
Hello,
under Ubuntu 11.04, I have exactly the same problem with my Actions Semiconductor Co., Ltd D-Wave 2GB MP4 Player / AK1025 MP3/MP4 Player. I followed the advice of tangchengguang but the problem is the same as jfca283 reported. Does anybody know how to solve it?

Thanks, flosn

---

