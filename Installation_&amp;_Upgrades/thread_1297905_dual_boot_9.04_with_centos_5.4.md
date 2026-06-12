---
title: "dual boot 9.04 with centos 5.4"
date: 2009-10-22
forum: Installation &amp; Upgrades
---

### Post by extendedping on 2009-10-22
well, I need to know rhel and thus would like to dual boot my pc with centos 5.4 which just came out. I was going to just use virt box or kvm but I have found I just don't like those methods (smaller screen slower performance etc). but after trying ubuntu for a few months there is no way I am giving it up as my main os...so...how can I do this and keep ubuntu as the main os? I have downloaded the latest gparted live cd and below is my fdisk -l and df -hP command output. 

root@ubuntu:~# fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x50c050bf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29164   234259798+  83  Linux
/dev/sda2           29165       30401     9936202+   5  Extended
/dev/sda5           29165       30401     9936171   82  Linux swap / Solaris
root@ubuntu:~# df -hP
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             220G  136G   74G  65% /
tmpfs                 1.9G     0  1.9G   0% /lib/init/rw
varrun                1.9G  324K  1.9G   1% /var/run
varlock               1.9G     0  1.9G   0% /var/lock
udev                  1.9G  148K  1.9G   1% /dev
tmpfs                 1.9G   88K  1.9G   1% /dev/shm
lrm                   1.9G  2.5M  1.9G   1% /lib/modules/2.6.28-15-generic/volatile

yea I know I should not run ubuntu as root but I do. anyway so I have plenty of space really only need say a 20 or 30 gb space for centos as all I will use it for is learning and using a few other linux kvm machines perhaps. 

I don't care which grub (centos or ubuntu) rules the land, I just want the easier of the easiest method of doing the dual boot and I do want ubuntu to be the "default" os. 

ok so I know I will have to shrink the ubuntu / partition, after that I am pretty much lost. I know centos will ask me to install or where to install the grub. I am not sure what to do there, do I not install a grub and then search for the centos installation from ubuntu (if ubuntu will still boot that is..). anyway in short I have never done this and wonder if the forum has any advice. btw I do not have a seperate hd to install...thanks in advance.

---

### Post by dstew on 2009-10-22
Yes, you need to shrink the Ubuntu / partition (/dev/sda1) to create space for CentOS. After you shrink it, create a new partition from the unallocated space, but leave it unformatted. Then, install CentOS into the new partition, and let the installer format the partition.

If you want to let CentOS install its boot loader, that is probably OK, it should identify your other OS's and create a boot menu for them.

Me personally, I would not install the new boot loader. I would create a new grub entry "by hand" for CentOS, by editing the Ubuntu /boot/grub/menu.lst file. You would need to put in the correct root, kernel and initrd arguments for the CentOS system though. If you know what these arguments should be, because you have examples of them, it shouldn't be too hard. The grub root command argument is just the partition that has the kernel image in it. If your new partition is /dev/sda3, the root will probably be (hd0,2). The kernel image should be in the root or /boot directory of the new CentOS system. The kernel command might need arguments after the kernel image statement, such as root=/dev/sda3. The initrd image should be in the same directory as the kernel image.

---

