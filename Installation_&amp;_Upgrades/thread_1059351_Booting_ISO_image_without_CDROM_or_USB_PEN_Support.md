---
title: "Booting ISO image without CDROM or USB PEN Support"
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by AchillesParis on 2009-02-03
I cannot get GRUB to boot the ubuntu v8.10 iso-image that I've copied onto the first partition of old 15gb disc I had lying around, which I've installed as the second harddrive, i.e. grub (hd1,0).  I've examined the v8.10 isolinux set up lcoated in /isolinux/textcfg and extracted the following grub menu item :

title ubtune LiveCD (hdb1)
root (hd1,0)
kernel	        /casper/vmlinuz file=/preseed/ubuntu.seed boot=casper
initrd	        /casper/initrd.gz 
boot

booting fails when it tries to mount the real root partition. From looking in the initrd.gz image, I've found that its failing in  'scripts/casper' stepping through the findlive_fs function therein.  I've tried specifying root=/dev/sdb1 with the same results. Also, I've tried converting the partition to syslinux setup (aka USB pendrive solns) and then chainloaded from GRUB - with the same result ie. can't find the live_fs.

I could just temporary install a CDROM from another PC, but I'd like the option of keeping this second harddrive partition as a mini easy-installer, eg down an iso, copy to the partition, examine the isolinux cfg and then add option to grub accordingly.

---

### Post by member on 2009-02-05
I have a very similar question. 

I have one harddrive with three partitions (A,B,C), of which only one is being used (OS X on partition A). The other two partitions are formatted as fat32 and are empty. I would like to use OS X to download linux distros and copy them to partition C and then, using a bootable USB flash drive, boot into linux (running from the USB flash drive and RAM) and install the distro image file(s) existing in partition C onto partition B to create a dual boot system (partitions A and B) 

The result would be a dual boot system (OS X and Ubuntu) with a partition available for storage of future linux distros. 

I have neither an internal or an external DVD ROM, nor a USB flash drive large enough to store the Ubuntu Live CD. (Hence my question) I am able to boot from a small (512MB) USB flash drive into Puppy Linux 4.10 and see the three partitions on the harddrive.

So the question is: How to install a local copy of Ubuntu 8.10 to a second partition using a "small" USB flash drive bootable to linux?

From browsing the internet. I know there are many out there buying external DVD drives and large USB flash drives to accomplish the same result. A satisfactory answer to this questions could save us a lot of time, money, and maximize the use of our existing equipment. 

Thanks,
Member.

---

### Post by avtolle on 2009-02-05
[https://help.ubuntu.com/community/Installation/#Standard%20installation](https://help.ubuntu.com/community/Installation/#Standard%20installation) contains many alternative methods for installing. FYI.

---

### Post by Pumalite on 2009-02-05
Installing from ISO file:
[http://ubuntuforums.org/showthread.php?t=316093](http://ubuntuforums.org/showthread.php?t=316093)

---

### Post by nikhilbhardwaj on 2009-10-20
for the live cd 
it may be possible
 
```
 
if you can specify the root as 
kernel /casper/vmlinuz root=/dev/ram0 aufs cdroot=/dev/sda1 looptype=squashfs max_loop=8 loop=/casper/filesystem.squashfs
initrd /casper/initrd.gz

```
 
what i mean to say is that if you can tell the kernel that the root is a squashfs file not a block
then it'll work
this works for gentoo and sabayon but may need a little tweaking for ubuntu

---

