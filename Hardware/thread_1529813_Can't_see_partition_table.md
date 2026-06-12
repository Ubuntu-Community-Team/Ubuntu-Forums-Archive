---
title: "Can't see partition table"
date: 2010-07-12
forum: Hardware
---

### Post by kay.one on 2010-07-12
I was tasked with fixing a friends ancient desktop, so decided to give xubuntu a try, booted using live cd and everything seems fine except I can't install to disk since xubuntu, mint, ubuntu can't see the partition table.

everything works fine if I boot using hiren boot cd, or windows but as soon as I go into ubuntu it fails to see the partition.

I'm guessing it might be the age of the motherboard/controller. its a [GA-5AX]("http://www.gigabyte.com/products/product-page.aspx?pid=1578&dl=1#sp") which I have updated to latest version of bios.
The hdd is a 8GB Fujitsu drive.


here are the results I get using different apps.

Dos/Windows/Acronis Disk Director: Everything works fine, can partition, read and write files.

Ubuntu Setup: I setup all the partitions but get 
Attempt to mount a file system with type ext2 in scsi1 (0,0,0) failed.

Gparted:  disk shows as unalocated space, I try to add partition but get can't add partition until I create a partition table. I tried creating a partition table and it doesn't have any effect.

Fdisk -l: Disk /dev/hdb doesn't contain a valid partition table
I create a new partition write the changes with 'w' but as soon as I close and reopen fdisk I get the same error.

cfdisk: same as fdisk.


is there anyway that I could get ubuntu/xubuntu/mint to install?

---

