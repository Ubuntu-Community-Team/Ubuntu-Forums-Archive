---
title: "LSI 9300-16i / HDIO_GET_IDENTITY failed / modifying disk id (udev?)"
date: 2016-02-12
forum: Hardware
---

### Post by Hammi on 2016-02-12
Hi,

I'm playing around with hardware for a new server. I want to setup a new raid, and I need to be able to identify individual disks in the case, e.g. if they should fail.
For that purpose, I looked around in /dev/disk/by-id, and found (yes, only 2 HDDs connected so far, only one of which is partitioned):

```
scsi-35000cca242d8480d
scsi-35000cca242d8492a
scsi-35000cca242d8492a-part1
```

I then looked on the disks and figured, that the serial number is not contained in the id. Actually, it appears the ID is totally unrelated to the serial. Bummer.
fdisk shows a disk id of 0x00000000 for each of these disks:

```
# fdisk -lu /dev/sda

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 6001.2 GB, 6001175126016 bytes
255 heads, 63 sectors/track, 729601 cylinders, total 11721045168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000
```

hdparm throws an error:
```
# hdparm -i /dev/sda

/dev/sda:
 HDIO_GET_IDENTITY failed: Invalid argument
```

Not sure if that is the reason for the strange disk-id. Smartctl is much better at reading the disk:

```
# smartctl -a /dev/sda
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.19.0-49-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Device Model:     HGST HUS726060ALE610
Serial Number:    NAHRE5SX
(...)
```

I tried installing the most recent Linux driver from LSI/Avago, but to no avail.

So my question is: How can I get Ubuntu to produce a disk ID containing the disk's serial? If that's not possible, how can I change the disk ID manually (once and for all)?

Gooling around, I found most people having these issues with USB disks. I also found one solution for USB, where they tell udev to import the USB ID instead: [http://birdslikewires.co.uk/no-to-hdio-get-identity-failed](http://birdslikewires.co.uk/no-to-hdio-get-identity-failed)

Would there be a way to import the serial that smartctl throws out into the disk-id as well?

Thanks for any hint![URL="http://birdslikewires.co.uk/no-to-hdio-get-identity-failed"]
[/URL]

---

