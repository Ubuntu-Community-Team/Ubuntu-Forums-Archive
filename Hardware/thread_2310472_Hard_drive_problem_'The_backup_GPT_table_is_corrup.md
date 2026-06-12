---
title: "Hard drive problem 'The backup GPT table is corrupt, but the primary appears OK'"
date: 2016-01-19
forum: Hardware
---

### Post by musicboy on 2016-01-19
The backup GPT table is corrupt, but the primary appears OK, so that will be used.
Disk /dev/sdc: 149.1 GiB, 160041884672 bytes, 312581806 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 17DB89A7-D738-448B-8B32-7DBE5B5A720D
skelm@theoffice:~$ sudo gdisk /dev/sdc
GPT fdisk (gdisk) version 1.0.0

Warning! Read error 5; strange behavior now likely!
Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

v    verify disk = 

Problem: The secondary header's self-pointer indicates that it doesn't reside
at the end of the disk. If you've added a disk to a RAID array, use the 'e'
option on the experts' menu to adjust the secondary header's and partition
table's locations.

Problem: main GPT header's current LBA pointer (1) doesn't
match the backup GPT header's alternate LBA pointer(312581805).

Problem: main GPT header's backup LBA pointer (312581805) doesn't
match the backup GPT header's current LBA pointer (1).
The 'e' option on the experts' menu may fix this problem.

Identified 3 problems!

---------------------------------------------------------------------------------------------------

K right this disk was a Mac OSX disk from a Mac Book Pro after I upgraded their hard drive for them and intsalled OSX onto that with time machine back up blah.

I've used this in a usb disk caddy so I am using it as an external drive to fix this.

I went into Gedit, delete the partitions, went to format in ext4 and it returned errors that there was no partition table.

Then tried to wipe over the disk, that returns errors. I then started using gdisk of which then I copied the primary GTP table to the back up in expert settings. But this did not solve the problem. 

It seems some how, some data is outside the size the disk and I am completely missing something?

Any help fixing this disk would be greatly appreciated, I was going to use this in a HTPC set up to just get it going for now.

Thanks for any help.

---

### Post by musicboy on 2016-01-22
97 views no ones replied? Anyone? Please?

---

