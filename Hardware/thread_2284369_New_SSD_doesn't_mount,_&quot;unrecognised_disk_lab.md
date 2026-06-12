---
title: "New SSD doesn't mount, &quot;unrecognised disk label&quot; (sda in live session)"
date: 2015-06-29
forum: Hardware
---

### Post by tptmrk on 2015-06-29
I replaced my HDD with a new Emtec SSD and ran a live session of 15.04 via USB. 
SSD is set to AHCI in bios and all tests check out there. 

sudo parted -l
Error: /dev/sda: unrecognised disk label
Model: ATA SATA SSD (scsi)
Disk /dev/sda: 240GB
Sector size (logical/physical): 512B/512B
Partition Table: unkown
Disk Flags:

(and it shows info for bootable USB drive)

Appreciate any help. I'm no expert and haven't been able to find this exact problem solved. Perhaps I just need to format the drive with another utility??? If this info helps, sda1 doesn't exist:

sudo mount /dev/sda1 /mnt
mount: special device /dev/sda1 does not exist

---

### Post by kerry_s on 2015-06-29
use gparted to create a partition table & format the drive.

gparted is on the live session.

---

### Post by tptmrk on 2015-06-29
Thanks! That did the trick.

---

