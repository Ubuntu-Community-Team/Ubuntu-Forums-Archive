---
title: "initrd raid problem on linux-k7 and 686 (386 ok)"
date: 2005-03-22
forum: Hardware &amp; Laptops
---

### Post by soul_rebel on 2005-03-22
I need a kernel with highmem support so it's one out of k7 and 686 but they both won't boot. I am getting something like this:

pivot_root no such file or directory
/sbin/init/: cannot open dev/console: no such file
Kernel Panic: Attempted to kill init!

the sata disks seem to be detected, so i think that the problem is the raid, infact i am using a raid0 root filesystem.
Everything is ok using linux-386 kernel, so I mounted both ramdisk and started to look at the differences. I found that the initrd-k7 does NOT have a binary called mdadm under /sbin which 386 has. I think this is the problem.

So here come the questions: 
(1) how do I configure mkinitrd to include that program? and 
(2) how do I generate a new ramdisk for a specified kernel?

man mkinitrd didn't solved 2 and helped a little for 1.

thanks for the help, I'll be helping newbies soon  8) bye

---

### Post by soul_rebel on 2005-03-23
I'll reply myself (after some study)

I installed linux-image updates today and after that also linux-386 refused to boot.

i found you can create a ramdisk using
#mkinitrd -o output-file [kernel-version]
so it's like 
#mkinitrd -o /boot/initrd.img.2.6.10-5-386 2.6.10-5-386

i have put "/sbin/mdadm" in /etc/mkinitrd/exe
and "md" and "raid0" in /etc/mkinitrd/modules
so those files were included in the ramdisk

Anyway that didn't solve the problem, so i had to boot from the ubuntu warty install cd.
Here is what i did:
follow installation procedure until partitioning
selected my raid configuration
escaped to a shell
modprobe md
modprobe raid0
mounted /dev/md/0 on a /mnt dir
mounted /mnt/boot
mounted /mnt/dev (-t devfs)
mounted /mnt/proc (-t proc)
chrooted in /mnt
symlinked /dev/md/0 to /dev/md0
created the ramdisks for every kernel
that makes it work: raid is detected on boot

I think we have a problem with the ramdisk creation... and i think it's something about this:
[B]normally i have /dev/md0 while ramdisk creation probably expect to have /dev/md/0
[/B]
Secondly man mkinitrd could be better with an example.

Hope this report could lead to a better Ubuntu. bye

---

