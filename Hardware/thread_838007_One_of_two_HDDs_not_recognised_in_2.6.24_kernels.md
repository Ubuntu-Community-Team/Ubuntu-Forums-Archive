---
title: "One of two HDDs not recognised in 2.6.24 kernels"
date: 2008-06-23
forum: Hardware
---

### Post by jamespetts on 2008-06-23
After upgrading to Hardy from Gusty, I found that the system would hang on starting up shortly after the "Ubuntu" loading screen was displayed, showing the progress bar moving backwards and forwards, rather than progressing, and the eventually dropping me out to "BusyBox", with only a ramdisk filesystem. The problem occurred when I tried to boot into any 2.6.24 kernel, but 2.6.22 kernels are fine.

I eventually found that the problem was that one of my two hard drives - the one with all of the Linux filesystem on it (the other being just for backups) - was not being recognised: it did not appear anywhere in /dev/disk. Only the one hard drive (/dev/sda/) appeared. /dev/sdb/, my main Linux disc, was nowhere to be found. My CD-ROM drive was detected.

Can anyone assist with what might be giving this problem? Both HDDs are SATA drives, and I am using a VIA mini-ITX EX1000G motherboard. Any help would be very much appreciated.

---

### Post by Zorael on 2008-06-23
'**sudo fdisk -l**', run from a live cd environment, actually only displays one disk? o.0

---

### Post by jamespetts on 2008-06-24
> **Zorael said:**
> '**sudo fdisk -l**', run from a live cd environment, actually only displays one disk? o.0

Thank you for your reply :-) I do not have a Hardy CD, as I upgraded from Gusty using the "upgrade distro" tool in "Update Manager". BusyBox doesn't let me use fdisk at all. When I use fdisk from my normal boot (the 2.6.22-14 kernel), I see both the HDDs.

---

