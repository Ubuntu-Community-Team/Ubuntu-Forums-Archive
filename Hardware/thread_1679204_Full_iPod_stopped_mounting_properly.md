---
title: "Full iPod stopped mounting properly"
date: 2011-01-31
forum: Hardware
---

### Post by JohnReid on 2011-01-31
Hi,

I filled up my iPod with songs and I may have unplugged it before ejecting it. It seems to work fine as an iPod but my mythbuntu 10.10 won't automount it any more. It sort of gets half-way there. When I plug it in, it turns up as a root file-system in /tmp. For example:
```
john@htpc:/media$ ls -l /tmp/ipodzGtIR8/
total 96
drwxr-xr-x 2 root root 16384 2000-02-10 22:38 Calendars
drwxr-xr-x 2 root root 16384 2000-02-10 22:38 Contacts
drwxr-xr-x 8 root root 16384 2000-02-10 22:38 iPod_Control
drwxr-xr-x 2 root root 16384 2000-02-10 22:38 Notes
drwxr-xr-x 3 root root 16384 2009-06-12 12:30 Photos
drwxr-xr-x 2 root root 16384 2000-02-10 22:38 Recordings

```I get these errors in dmesg:
```
[ 2997.826468] usb 1-1.1: USB disconnect, address 6
[ 2998.771439] FAT: bread failed in fat_clusters_flush
[ 2999.589041] usb 1-1.1: new high speed USB device using ehci_hcd and address 7
[ 2999.707128] scsi7 : usb-storage 1-1.1:1.0
[ 3000.379578] usb 1-1.1: USB disconnect, address 7
[ 3000.616059] usb 1-1.1: new high speed USB device using ehci_hcd and address 8
[ 3000.737786] scsi8 : usb-storage 1-1.1:1.0
[ 3001.741381] scsi 8:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 3001.742603] sd 8:0:0:0: Attached scsi generic sg2 type 0
[ 3001.760215] sd 8:0:0:0: [sdd] Spinning up disk...
[ 3008.964325] usb 1-1.1: USB disconnect, address 8
[ 3009.969797] .ready
[ 3009.969938] sd 8:0:0:0: [sdd] READ CAPACITY failed
[ 3009.969943] sd 8:0:0:0: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 3009.969949] sd 8:0:0:0: [sdd] Sense not available.
[ 3009.969976] sd 8:0:0:0: [sdd] Write Protect is off
[ 3009.969983] sd 8:0:0:0: [sdd] Mode Sense: 53 02 00 00
[ 3009.969986] sd 8:0:0:0: [sdd] Assuming drive cache: write through
[ 3009.970300] sd 8:0:0:0: [sdd] READ CAPACITY failed
[ 3009.970305] sd 8:0:0:0: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 3009.970312] sd 8:0:0:0: [sdd] Sense not available.
[ 3009.970342] sd 8:0:0:0: [sdd] Assuming drive cache: write through
[ 3009.970348] sd 8:0:0:0: [sdd] Attached SCSI removable disk
[ 3026.911795] usb 1-1.2: new high speed USB device using ehci_hcd and address 9
[ 3027.039773] scsi9 : usb-storage 1-1.2:1.0
[ 3028.041849] scsi 9:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 3028.042668] sd 9:0:0:0: Attached scsi generic sg2 type 0
[ 3028.077738] sd 9:0:0:0: [sdd] Spinning up disk....ready
[ 3031.560651] sd 9:0:0:0: [sdd] 39023511 4096-byte logical blocks: (159 GB/148 GiB)
[ 3031.561267] sd 9:0:0:0: [sdd] Write Protect is off
[ 3031.561273] sd 9:0:0:0: [sdd] Mode Sense: 68 00 00 08
[ 3031.561277] sd 9:0:0:0: [sdd] Assuming drive cache: write through
[ 3031.563220] sd 9:0:0:0: [sdd] 39023511 4096-byte logical blocks: (159 GB/148 GiB)
[ 3031.563708] sd 9:0:0:0: [sdd] Assuming drive cache: write through
[ 3031.563715]  sdd: sdd1
[ 3031.752351] sd 9:0:0:0: [sdd] 39023511 4096-byte logical blocks: (159 GB/148 GiB)
[ 3031.752942] sd 9:0:0:0: [sdd] Assuming drive cache: write through
[ 3031.752947] sd 9:0:0:0: [sdd] Attached SCSI removable disk
[ 3047.007886] FAT: Directory bread(block 19082) failed
[ 3047.007898] FAT: Directory bread(block 19083) failed
[ 3047.007908] FAT: Directory bread(block 19084) failed
[ 3047.007918] FAT: Directory bread(block 19085) failed
[ 3047.007941] FAT: Directory bread(block 19082) failed
[ 3047.007947] FAT: Directory bread(block 19083) failed
[ 3047.007953] FAT: Directory bread(block 19084) failed
[ 3047.007959] FAT: Directory bread(block 19085) failed

```The "READ CAPACITY failed" part seems particularly worrying.

If I've understood what I've read correctly. /dev/sdd should be the whole disk. /dev/sdd1 should be the partition with the firmware on it and /dev/sdd2 is where my tunes are stored. I'm not getting any /dev/sdd2 at all, just /dev/sdd and /dev/sdd1. Have I stuffed my ipod up? What can I do to check and/or repair it?

I can cd to the directories in the /tmp mount point and see some of the music files but some are empty...
```
john@htpc:/tmp/ipodzGtIR8/iPod_Control/Music/F02$ pwd
/tmp/ipodzGtIR8/iPod_Control/Music/F02
john@htpc:/tmp/ipodzGtIR8/iPod_Control/Music/F02$ ls -l | head
total 2863424
-rwxr-xr-x 1 root root        0 2011-01-16 11:54 01 Arcangelo Corelli.mp3
-rwxr-xr-x 1 root root  6705401 2011-01-16 11:35 01 - Black & Gold.mp3
-rwxr-xr-x 1 root root  6824124 2011-01-16 11:28 01 I Know You Got Soul.mp3
-rwxr-xr-x 1 root root        0 2011-01-16 11:53 01 - Lay Back Down.mp3
-rwxr-xr-x 1 root root        0 2011-01-16 11:52 01 - Masenqo.mp3
-rwxr-xr-x 1 root root  7969221 2011-01-16 11:35 01 - My Dog's Still Walkin'.mp3
-rwxr-xr-x 1 root root        0 2011-01-16 11:55 01 Parce Mihi Domine.mp3
-rwxr-xr-x 1 root root        0 2011-01-16 12:06 01 Tranquil Passage.mp3
-rwxr-xr-x 1 root root        0 2011-01-16 12:02 01 - Various Artists - V~JL.mp3

```fdisk gives me:
```
john@htpc:/media$ sudo fdisk -l
... <snip> ...
Disk /dev/sdd: 159.8 GB, 159840301056 bytes
26 heads, 50 sectors/track, 30018 cylinders
Units = cylinders of 1300 * 4096 = 5324800 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       30019   156093788    b  W95 FAT32
Partition 1 does not start on physical sector boundary.

```Any help appreciated!

Thanks,
John.

---

### Post by JohnReid on 2011-02-02
bump (hopefully)

---

