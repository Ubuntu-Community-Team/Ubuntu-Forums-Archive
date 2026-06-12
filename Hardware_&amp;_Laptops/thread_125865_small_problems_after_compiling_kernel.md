---
title: "small problems after compiling kernel"
date: 2006-02-05
forum: Hardware &amp; Laptops
---

### Post by keebler411 on 2006-02-05
In another thread I posted about having problems getting the Promise sata 300 tx4 controller card to work.  While I been mostly successful I still have a few minor problems after compiling a new kernel.  I made a completely monolithic kernel except for modules related to LVM/RAID which are needed by initramfs (I have not seen this explicitly mentioned anywhere BTW).  My sata module is autoloaded from /lib/modules/2.6.12-sata/sata/ulsata2.ko  I use the classic method to compile a kernel.  I don't grok make-kpg yet :)

I get the following three non-fatal errors when booting up:

1) modprobe fatal: could not load /lib/modules/2.6.12-sata/modules.dep..... ;of course it actually exists
2) any entries in fstab related to disks on the sata controller fail; however I can mount them manually after logging in as root
3) /dev/cdrom: open failed error shortly after error 1

I've tried the following to solve problem 2 with no luck:
1) rebuilding initramfs with ulsata2.ko in the module directory
2) adding ulsata2.ko to /etc/modules
3) adding ulsata2.ko to /etc/mkinitramfs/modules and rebuilding initramfs

I also get this error when shutting down:
4) /lib/lsb/init-functions: line 236: /usr/bin/tput: no such file or directory; it does exist; could be related to error 1 above

Any help would be appreciated.  Although not all the problems listed are directly related to getting the sata controller working I'd like to solve them just in case because I plan on posting a HOW-TO.  Thanks.

keeb

---

### Post by keebler411 on 2006-02-05
I solved problem #2 like this:

-recompiled kernel to make ext2/ext3 modules; I was getting a non-fatal error I didn't document before
-compiled sata driver
-copied ulsata2.ko to /lib/modules/VERSION/scsi
-added md, dm_mod, ulsata2, ext2, ext3, to /etc/mkinitramfs/modules
-created initramfs and actually copied it to /boot this time :O
-fixed syntax error in fstab

I think problems 1&3 are related to LVM but I can live with them since they don't seem to be fatal (for now)

keeb

---

