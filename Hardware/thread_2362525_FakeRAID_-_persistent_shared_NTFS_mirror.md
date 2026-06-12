---
title: "FakeRAID - persistent shared NTFS mirror"
date: 2017-05-29
forum: Hardware
---

### Post by mwave6 on 2017-05-29
Hey All,

I'm a long-time Ubuntu & Mint user trying to set up RAID-1 mirroring for the first time under Linux. I know that "fakeRAID" and mdadm are discussed extensively across linux forums from Arch to Zorin. However, I still haven't come across a complete solution for what I'm attempting:

I've got a dual boot EFI system with Windows 10 & Mint v18.1 (equivalent of Xenial). OSes both on a 320gb drive. Also have (2) identical WD 3TB drives. Using the AMD software to combine them into a single 3TB NTFS mirror under Windows. However, both drives appear as separate units under Linux - which is to be expected.

This article has been the most helpful thus far and when I run the command below I do, in fact, achieve a single logical drive (after 4-5hrs) and the dual 3TB drives are gone.
[https://superuser.com/questions/377646/how-do-i-mount-a-software-raid1-mirror-created-by-windows-in-linux-using-mdadm](https://superuser.com/questions/377646/how-do-i-mount-a-software-raid1-mirror-created-by-windows-in-linux-using-mdadm)

mdadm --build /dev/md0 --level=1 --raid-devices=2 /dev/sdc2 /dev/sdd2

mount /dev/md0 /mount/raid

The article mentioned using "build" instead of "create" so as to be non-destructive of existing data. I've deliberately not placed important data on the volume until I've got the configuration correct. While the commands above work perfectly, the RAID volume is gone upon the next reboot. I am unclear on what config file(s) need modified and how. I've seen discussion of using "mdadm --assemble", modifying RAIDTAB or FSTAB, internal & external superblock metadata, etc. However, none of these detect that a RAID volume ever existed.

Same with "mdadm --detail --scan". It's as if no RAID sets were ever created. Does anyone out there know what add'l steps I should be taking for this volume to persist?

Many thanks in advance!!!

---

### Post by mwave6 on 2017-06-03
I will add here that using mdadm --build produces an array that lacks a UUID that can be applied in mdadm.conf.

Does anyone have a suggestion for a way to generate some sort of handle for this array to persist?

---

