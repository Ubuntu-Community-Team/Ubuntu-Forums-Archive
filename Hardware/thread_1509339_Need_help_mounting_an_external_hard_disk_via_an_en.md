---
title: "Need help mounting an external hard disk via an enclosure (with a password)"
date: 2010-06-14
forum: Hardware
---

### Post by weijie90 on 2010-06-14
Hi all,

My old laptop is faulty (the graphics card conked out) and I got a new laptop. I bought an SATA-to-USB external hard drive enclosure to get my data off the old laptop's hard drive, but I can't mount anything on it. That hard drive has a BIOS-set password, grub in the MBR, as well as a mix of both NTFS and ext3 partitions.

I know what the password is.

How should I get my data? Any help would be highly appreciated. Thank you!

---

### Post by mikewhatever on 2010-06-14
What OS is on the new laptop? What happens when you connect the hard drive? What happens exactly when you try mounting a partitions on that hard drive? Any errors? With the hard drive connected, post the output of **sudo fdisk -l**.

---

### Post by weijie90 on 2010-06-14
The new laptop is dual-booting Kubuntu 10.04 and Windows 7.

sudo fdisk -l output only shows my internal hard drive.

[http://pastebin.com/XRWz63ni](http://pastebin.com/XRWz63ni)

dmesg output:

[http://pastebin.com/xzaJjMFL](http://pastebin.com/xzaJjMFL)

Thanks!

---

### Post by weijie90 on 2010-06-14
Solved.

I just removed the password from the disk with my old laptop. Fortunately, the faulty screen survived long enough for me to do so.

I did try to plug the hard disk into my new laptop's SATA bay, but I couldn't use it to remove the password. Could be that the two BIOSes or motherboards set the password differently.

---

