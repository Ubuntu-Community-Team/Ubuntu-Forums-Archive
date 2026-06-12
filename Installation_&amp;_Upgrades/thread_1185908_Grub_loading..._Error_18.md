---
title: "Grub loading... Error 18"
date: 2009-06-12
forum: Installation &amp; Upgrades
---

### Post by ThewhiteLynx on 2009-06-12
I just installed Ubuntu 9.04, and when I tried to boot I got:

GRUB Loading stage1.5.

GRUB loading, please wait...
Error 18

What does this mean?

---

### Post by Zero++ on 2009-06-12
[B]Here's what it means. I'm having the exact same problem. No one was able to help so far. Let me know if you hear anything. 
 [/B]

** Error 18 **

 ***Error 18**: Selected cylinder exceeds maximum supported by BIOS* 
This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB on others.). In more practical terms this means the BIOS is unable to start executing the kernel because the kernel is not located within the block it can access at boot up time. 
This can be circumvented by creating a boot partition at the beginning of the disk that is completely within the first 1023 cylinders of the harddrive. This partition will contain the kernel. 
 The kernel itself does not suffer from the same limitations as the BIOS so after the BIOS has loaded the kernel the kernel will have no problem accessing the whole harddrive. Newer BIOSes will automatically translate the harddrives size in a way that it can be completely contained within the first 1023 cylinders and hence modern computers do not suffer from this problem. 
The same error can happen when the BIOS detects a disk in a different way as Linux does. This can happen when changing motherboards or when moving a GRUB-bootable disk from one computer to another. If this happens, just boot with a GRUB floppy, read the C/H/S numbers from the existing partition table and manually edit the BIOS numbers to match. If using a SUSE linux and installing on VM Ware this problem is solved by creating a small partition at the very beginning of the harddisc, and mounting it as /boot. 

Read more: [http://wiki.linuxquestions.org/wiki/GRUB#Debian#ixzz0IGRVi7G7&C](http://wiki.linuxquestions.org/wiki/GRUB#Debian#ixzz0IGRVi7G7&C)

---

### Post by Zero++ on 2009-06-12
I figured it out and just got mine up and running.

When you are partitioning your HDD select the manual partition option.

Delete any of the present partitions (i am assuming that you do not have a windows partition that you want to keep in tact)

Make a small (i did 1 gig) partition and in the mount menu set it to /boot

Next make your main partition (saving 2 - 3 gigs for swap) and in the mount menu set it to /

finally make a swap partition in the last 2-3 gigs of free space

Your OS should boot. I'm duel booting with Windows XP and this method worked just fine. 

If you need to check your partitions or set the /boot partition to boot (it should do it automatically) download a program called GParted. It's  a linux based partitioning program and allows you to set which partition you want to boot from among other great options.

---

### Post by ThewhiteLynx on 2009-06-12
> **Zero++ said:**
> I figured it out and just got mine up and running.

When you are partitioning your HDD select the manual partition option.

Delete any of the present partitions (i am assuming that you do not have a windows partition that you want to keep in tact)

Make a small (i did 1 gig) partition and in the mount menu set it to /boot

Next make your main partition (saving 2 - 3 gigs for swap) and in the mount menu set it to /

finally make a swap partition in the last 2-3 gigs of free space

Your OS should boot. I'm duel booting with Windows XP and this method worked just fine. 

If you need to check your partitions or set the /boot partition to boot (it should do it automatically) download a program called GParted. It's  a linux based partitioning program and allows you to set which partition you want to boot from among other great options.

I tried that but it didn't work

---

### Post by Zero++ on 2009-06-14
You could try shrinking the size of the /boot partition down if you made a 1 gig partition like I did. Maybe 500 or even 100 mb. 

Also because it is a BIOS problem you could try running the Live version of Ubuntu and flashing your BIOS with the newest verstion.

---

