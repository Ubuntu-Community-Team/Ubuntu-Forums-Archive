---
title: "trying to run Ubuntu Live CD on machine w/ Ubuntu 8.10"
date: 2008-12-20
forum: Installation &amp; Upgrades
---

### Post by jpauld on 2008-12-20
I'm a newcomer to linux with Ubuntu 8.10 successfully installed.  It works great!  My problem is I want to install XP.  In order to do this I am trying to boot using the the live cd version of Ubuntu so that I can make an ntfs partition.  I keep getting a message window that says I/O error Error reading boot CD Reboot or something like the following:

Boot from (hd0,0)ext3 6948b75b-31b3-467c-887-7cb10c323efe
Starting up ...
Loafding, please wait...
uplash: Setting mode 1920x1440 failed
uplas: Using mode 1600x1200
Gave up waiting for root device.  Common problems:
 - Boot args (Cat /proc.cmdline)
    - Check rootdelay= (didsystem wait long enough?)
    - Check root=(did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
Alert! /dev/disk/by-uuid/6948b75b-31b3-467c-887f-7cb10c323efe does not exist. Dropping to a shell


BusyBox v1.10.2 (Ubuntu 1:1.10.2-ubuntu6) build-inshell (ash)
Enter 'help' for a list of built-in commands.

(Initramfs)  [  54.496336]  sd 2:0:0:0: [sda]  Assuming drive cache: write through [  54.515270]  sd 2:0:0:0:  [sda]  Assuming drive cache: write through

(initramfs)

Hard Drive info:

Model: ATA WDCWD1600jb-00E
Size: 149.05GiB
Path: /dev/sda

DiskLabel Type: msdos
Heads: 255
sectors/Track: 63
Cylinders: 19457
Total Sectors 312576705

disk is partitioned as follows:

Partition      Filesystem    Mountpoint  Size   used   unused
/dev/sda1 ext3 ext3          /           146.89 5.75GiB  141.14G
/dev/sda2 extended                        2.16GiB   -       -
   /de/sda5 linux-swap                    2.16GiB   -       -

Help please

Paul

---

### Post by hal8000 on 2009-01-18
You may already have solved this now, but you dont have to use the live CD to make an ntfs partition.

Boot into intrepid then issue

sudo mkfs.ntfs /dev/sda1

replace sda1 with the partition you inrend to use for XP, one problem windows always needs a primary partition and I believe it has to be first partition, so you may have to move Ubuntu to make room for XP.

---

