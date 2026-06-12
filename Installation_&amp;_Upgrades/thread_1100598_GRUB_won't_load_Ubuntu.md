---
title: "GRUB won't load Ubuntu"
date: 2009-03-19
forum: Installation &amp; Upgrades
---

### Post by jessel on 2009-03-19
Hello,

I screwed up my GRUB installation and I cannot get it working again. Any help would be greatly appreciated.

I think my problem is that I don't have a linux kernel anymore. I have read through the GRUB manual a few times now and I still do not see the answer...

DRIVE SETUP
======================
sda1: 10GB, unused partition
sda2: 130GB, ntfs, used for storage
sda3: 9GB, Ubuntu 8.10, mounted as /
sda4: 1GB, swap
sdb: 20GB, windows

WHAT HAPPENED
======================
I reformatted sda1 and reinstalled GRUB. Somehow when I reinstalled GRUB I lost some files. THERE IS NO KERNEL in / or /boot, /vmlinuz is a broken link...

WHAT I HAVE DONE TO REINSTALL GRUB
====================================
 ATTEMPT 1) -> boot install cd, enter trial mode and then open terminal (see grub_1.txt)
  # sudo grub
   > sudo root (hd0,2)
   > setup (hd0)
   > quit
  restart the computer, and GRUB loads but will not load Ubuntu
 ATTEMPT 2) -> boot install cd, enter trial mode and then open terminal (see grub_2.txt)
  # sudo grub
   > root (hd0,2)
   > setup (hd0,2)
   > quit
  restart the computer, and GRUB loads but will not load Ubuntu
 ATTEMPT 3) -> boot install cd, enter trial mode and then open terminal (see grub_3.txt)
 # sudo mount -t ext3 /dev/sda3 /mnt
 # sudo grub-install --root-directory=/mnt /dev/sda3
  restart the computer, and GRUB loads but will not load Ubuntu


Thanks,

Jesse

---

### Post by MasterSander on 2009-03-19
Seems like there's nothing wrong with GRUB, but you're saying you don't have a kernel, so ubuntu won't boot, I'd reinstall ubuntu after backing up your files with the live cd

---

### Post by jessel on 2009-03-24
Well, I got back into my system.

I used my unused partition and installed a system on it. 

Then I copied the kernel and initrd image back to the system that I couldn't boot.

Then I rebooted, when I got the GRUB menu I entered the GRUB command line mode.

> root (hd0,2)
> kernel /vmlinuz... root=/dev/sdb3 ro
> initrd /initrd...
> boot

A couple comment on the kernel command that hung me up:
 + the root=/ is critical
 + it took me a little while for me to figure out not to use /dev/sda3, which would make more sense to me, but it must be because the menu.1st has a windows entry in which i use the map command?

To re-install GRUB, open a terminal:
# grub-install /dev/sdb     (make sure you are installing on the correct drive!!!)

note: you do NOT want "install-grub /dev/sdb3"

from this point you can reboot and configuration of grub is done by editing menu.1st, then "update-grub"

---

