---
title: "HELP! Got ext2 superblocks on my ext3-formated HDD"
date: 2007-07-14
forum: Hardware &amp; Laptops
---

### Post by mrgod on 2007-07-14
Hi :)

Running ubuntu 7.04 with all updates.
I got a problem with my external disk. It is formated with ext3 and mounted in ext3, working fine for a while now. And yesterday it just stopped. But when I checked it with testdisk, it shows that the disk contains only ext2 superblocks :confused:

I think the reason to this is that I ran for some months ago the e2fsck to correct a looping folders on the disk. And it worked fine after that.

Is there anyway I can write new ext3-superblocks or convert the blocks to ext3-superblocks (I assume that ext3 formated disks should have ext3-superblocks)?
When I try mount:
sudo mount /dev/sda1 /media/500g
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

dmesg:
  533.995135] usb 3-3: new high speed USB device using ehci_hcd and address 4
[  534.129620] usb 3-3: configuration #1 chosen from 1 choice
[  534.130125] scsi1 : SCSI emulation for USB Mass Storage devices
[  534.130190] usb-storage: device found at 4
[  534.130193] usb-storage: waiting for device to settle before scanning
[  539.136953] usb-storage: device scan complete
[  539.138832] scsi 1:0:0:0: Direct-Access     WDC WD50  WD-WCANU1737457 2E09 PQ: 0 ANSI: 2 CCS
[  539.142425] SCSI device sda: 976773168 512-byte hdwr sectors (500108 MB)
[  539.143158] sda: Write Protect is off
[  539.143162] sda: Mode Sense: 00 38 00 00
[  539.143165] sda: assuming drive cache: write through
[  539.144332] SCSI device sda: 976773168 512-byte hdwr sectors (500108 MB)
[  539.145035] sda: Write Protect is off
[  539.145039] sda: Mode Sense: 00 38 00 00
[  539.145042] sda: assuming drive cache: write through
[  539.145047]  sda: sda1
[  539.158446] sd 1:0:0:0: Attached scsi disk sda
[  539.158497] sd 1:0:0:0: Attached scsi generic sg0 type 0
[  987.184989] EXT2-fs error (device sda1): ext2_check_descriptors: Block bitmap for group 2 not in group (block 524288)!
[  987.185001] EXT2-fs: group descriptors corrupted!
[ 1035.211243] EXT2-fs error (device sda1): ext2_check_descriptors: Block bitmap for group 2 not in group (block 524288)!
[ 1035.211255] EXT2-fs: group descriptors corrupted!


I also get an error when I boot the Ubuntu 7.04 on that disk, saying that the ext2 is something wrong with, type su-pass to do a diskcheck. I have skipped this cause the disk is in ext3.... I can't loose any data on this disk..

I really need help on this one.. Thanx for all help :)

---

### Post by mrgod on 2007-07-15
I've tried fsck.ext3 to check the disk, but is just goes in loop with the same groups.
Maybe this is the wrong forum... suggestions?

---

### Post by nhooey on 2007-11-04
Did you ever figure this out? I'm having the same problems with my drive...

---

### Post by tobycatlin on 2008-01-12
ditto i have the same problem

---

