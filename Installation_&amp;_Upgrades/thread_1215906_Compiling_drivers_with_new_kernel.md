---
title: "Compiling drivers with new kernel"
date: 2009-07-17
forum: Installation &amp; Upgrades
---

### Post by J. Jaybird on 2009-07-17
I have an issue with compiled drivers and new kernels.  My Mythbuntu 9.04 64-bit system boots from a Highpoint 2310 RAID card in a RAID-5 configuration. I am relatively new to Linux, but am a competent windows guy.  After doing a ton of research (special thanks to Stant0n here) I finally got my system up and running.  I do not have the box perpetually connected to the net, only periotically connecting and upgrading.  During my last patching session, I pulled down the -13 kernel update.  The update went fine, but when I rebooted, I could not boot into the new kernel, because the boot driver for my raid array was not present in the new kernel.  The -11 kernel worked good, so I was able to work through that, but I need to learn how to update my drivers in the future.  I have tried, but keep falling short on getting this to work right.  Here is my proceedure to do a fresh install of *ubuntu.  Could someone help me find the steps to compile the drivers for an updated kernel?  

Here are my steps to install from scratch.

1)Boot with Live disc
2)Copy downloaded driver tarball to /tmp
3)Open terminal
4)sudo rmmod sata_mv
5)cd /lib/modules/%kernel%/kernel/drivers/ata
6)sudo rm sata_mv.ko
7)cd /tmp
8)tar xvf %tarballname%
9)ls and make note of the expanded directory %x-dir% 
10) cd %x-dir%/product/
11) ls and make note of %x-dir2%
12) cd %x-dir2%/linux
    1.So a condensation of steps 9-12 from a previous install would be:
cd rr231x_0x-linux-src-v2.4/product/rr2310pm/linux
13) sudo make
14) ls and note %kofile% made
15) sudo insmod -p %kofile%
16) sudo depmod -ae
17) Use gparted to verify disk present
18) Use Ubuntu Installer- Be sure not to reboot
19) sudo mount /dev/sda1 /target
20) cd /tmp
21) cp -r %x-dir% /target/tmp
22) sudo chroot /target
23) umount proc
24) umount sysfs
25) mount
26) mount -t proc proc /proc
27) mount -t sysfs sysfs /sys
28) ln /usr/sbin/mkinitramfs /usr/sbin/mkinitrd
    1.this is due to highpoint specifically calling mkinitramfs.  It works.  I am not expert enough to know the details of why.
29) cd /tmp/%x-dir1%/product/%x-dir2%/linux
30) make clean
31)make install
32)exit
33)Reboot.

Any help would be appreciated!
J. Jaybird

---

