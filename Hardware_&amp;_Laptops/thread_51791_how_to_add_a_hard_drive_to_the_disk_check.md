---
title: "how to add a hard drive to the disk check?"
date: 2005-07-25
forum: Hardware &amp; Laptops
---

### Post by sal on 2005-07-25
i have a second hdd (used for personal data storage) set up on /dev/hdb1 mounted as
/mnt/hdb1

it is formated as an ext3 partition.

what i want to know is how to get the disk check that happenes after a cetain amount of system boots to check it. currently the only thing the disk check checks is:
/ (root) and /home

do i have to change something in /etc/fstab to get the disk to be checked?
TIA

---

### Post by grim42 on 2005-07-25
EDIT: what I said previously was wrong.

See post below by mo x.

Quote from fstab man:
> The sixth field, (fs_passno), is used by the fsck(8) program to determine the order in which filesystem checks are done at reboot time. The root filesystem should be specified with a fs_passno of 1, and other filesystems should have a fs_passno of 2. Filesystems within a drive will be checked sequentially, but filesystems on different drives will be checked at the same time to utilize parallelism available in the hardware. If the sixth field is not present or zero, a value of zero is returned and fsck will assume that the filesystem does not need to be checked.

---

### Post by mo_x on 2005-07-25
I think you have to put 2 in the sixth column of your /etc/fstab file. See the fstab man page.

---

