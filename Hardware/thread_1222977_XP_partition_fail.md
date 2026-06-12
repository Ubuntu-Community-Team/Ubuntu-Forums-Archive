---
title: "XP partition fail"
date: 2009-07-25
forum: Hardware
---

### Post by claw_atticas on 2009-07-25
My computer is dual-booting XP and Ubuntu. My main C: drive (No operating system, just storage) is on one partition, I have a 1GB FAT32 partition to copy files between Linux and XP (Without using an SD card or something), and on an extended partition is my NTFS XP installation partition, Linux Ext3 partition, and Linux Swap partition.

It was working fine last night, but when I booted it up this morning and tried to load Windows through GRUB, it said "Invalid or unsupported executable format". I found out that was a GRUB error, so I tried fixing XP's MBR by going into Windows Recovery, and typing 'FIXMBR', it said it was fixed, and I rebooted, to which it said "Could not load operating system" or something like that...

So I repaired the GRUB, went into GParted, and all my partitions are okay, except for my NTFS C: drive (The storage one, D: is my XP installation partition), to which its filesystem was "Unknown". Under Information, it reads > Unable to detect filesystem!

I know it's not a hard drive failing, otherwise all the other partitions would have the same problem (I only have one HDD, and it's on a laptop), and a few weeks back HDD Health said my HDD was at 100% health.

I type fdisk -l or fdisk -lu, and it says > cannot open /dev/sda
I try to mount the drive as NTFS. and it reads
> NTFS signature is missing.
Failed to mount '/dev/sda2': Invalid argument
The device '/dev/sda2' doesn't have a valid NTFS.

[edit] I tried one more thing, typing 'FIXMBR', to fix XP's master boot record, then typed 'FIXBOOT', and telling it to boot from my D: drive (My Windows drive), and now when I reboot, it tells me "No bootable devices"

---

