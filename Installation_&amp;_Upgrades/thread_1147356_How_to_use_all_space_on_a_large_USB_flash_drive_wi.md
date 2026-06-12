---
title: "How to use all space on a large USB flash drive with Remix installed ?"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by JackD on 2009-05-03
The Jaunty Remix .img for a flash drive install is incredibly useful. It boots fast, and is a tremendous demo for the "what-is-ubuntu" crowd that doesn't want to learn a different GUI from their Windows environment.

But, the .img file lays down a weird format that prevents using any space on the flash drive > 1 G. This means,

[LIST]
[*]I can't use a faster flash drive efficiently (most of the faster drives are larger)
[*]I can't use the Remix flash drive to store other data files
[/LIST]

I tried creating a 1G partition and writing the image myself (something like, $sudo dd if=<image file> of=/dev/sdb1

It wrote, but it won't boot. Also, if I look at the structure of Remix on a flash drive, through sfdisk, the layout isn't standard (using hpfs/ntfs for some sort of sub-partition that isn't exposed through other partitioning tools, like parted).

How can I install Remix, and still use a flash drive for storing data?

---

### Post by Brandon Williams on 2009-05-03
I haven't tried this myself, but it seems to me that you ought to be able to mount the .img file as a loop device and then copy the file system over to a partition that you created. I think you would need to use syslinux to make your custom partition bootable.

I'm not sure about all the mechanics, but it should be pretty similar to the old manual method of making a bootable USB stick from an live ISO. There are instructions for the manual method using an ISO [here](http://www.pendrivelinux.com/usb-ubuntu-804-persistent-install-from-linux/). There are instructions for mounting a .img file [here](http://www.andremiller.net/content/mounting-hard-disk-image-including-partitions-using-linux). This image seems like it might not use a partition table at all, which means that you might be able to simply mount it: 'sudo mount -o loop,ro unr-image-file.img /mnt'

This is just a brain dump of some things I've been thinking to try. I haven't gotten around to doing it yet, though.

---

### Post by JackD on 2009-05-04
Hm, Brandon, I'm not sure that mounting the img and copying is any different that using DD right into the partition. I have to think about it. Thanks for the idea (I'm aware of the pendrive solution, but not the other link for an .img file).

It's weird to me, that no one else is asking, but then maybe it's not a big deal to others.

Thanks, Brandon

---

### Post by Brandon Williams on 2009-05-05
Your right. There should be no difference between using dd and copying the files over.

Following that realization, I did the following:
[LIST=1]
[*]use fdisk to create 2 partitions
[LIST]
[*]one that is rough 1GB
[*]another that uses up the rest of the flash drive
[/LIST]
[*]dd if=ubuntu-9.04-netbook-remix-i386.img of=/dev/sd*X*1
[*]mkfs for /dev/sd*X*
[*]sudo install-mbr /dev/sd*X*
[/LIST]

I now have a UNR flash drive that I can boot from that also allows me to use the rest of the flash drive. The next thing I want to figure out is how to make the flash-drive UNR persistent.

I'm going to look at what usb-creator does to make an install persistent and see if I can do the same for this install.

---

### Post by Brandon Williams on 2009-05-05
I finally got this working. I have a 2GB USB key set up as a persistent install with a separate 500MB partition for file storage.

Here's what I did:
[LIST=1]
[*] use fdisk to create two partitions on the usb key
[LIST]
[*] 1 1.5GB FAT16 partition (/dev/sdb1) ... the extra space is to allow enough room for a casper-rw file
[*] 1 Linux EXT partition of the remaining size (/dev/sdb2)
[/LIST]
[*] make the filesystems on the partitions
[LIST]
[*] sudo mkfs.vfat -F 16 -n unr-904 /dev/sdb1
[*] sudo mkfs.ext2 -b 4096 -L data-storage /dev/sdb2
[/LIST]
[*] mount the image and the DOS partition
[LIST]
[*] sudo mount -o loop ubuntu-9.04-netbook-remix-i386.img ./IMG
[*] sudo mount /dev/sdb1 ./DOS
[/LIST]
[*] make a copy of  /usr/share/usb-creator/install.py and modify it as per the following diff
=====================================================
79,82c79,82
<     popen(['rm', '-rf', '%s/syslinux' % target])
<     popen(['mv', '%s/isolinux' % target, '%s/syslinux' % target])
<     popen(['mv', '%s/syslinux/isolinux.cfg' % target,
<             '%s/syslinux/syslinux.cfg' % target])
---
>     #popen(['rm', '-rf', '%s/syslinux' % target])
>     #popen(['mv', '%s/isolinux' % target, '%s/syslinux' % target])
>     #popen(['mv', '%s/syslinux/isolinux.cfg' % target,
>     #        '%s/syslinux/syslinux.cfg' % target])
100c100
<                         line.insert(pos, 'cdrom-detect/try-usb=true')
---
>                         #line.insert(pos, 'cdrom-detect/try-usb=true')
=====================================================
[*] sudo install-mbr /dev/sdb1
    (this is probably not necessary, but I'm not certain)
[*] sudo syslinux -sf /dev/sdb1
[*] sudo ./install.py -s ./IMG -t ./DOS -p 256
[/LIST]

---

### Post by JackD on 2009-05-06
Ah. that is a great hack ! Thanks ! Now, I can demo (and use) Remix and have any other tools available. Very cool.

---

### Post by Brandon Williams on 2009-05-06
I'm glad you find it useful.

FWIW ... I opened a [launchpad bug](https://bugs.launchpad.net/bugs/372252) suggesting that it should be easier to create a persistent UNR install on a USB. It would probably be good to get comments from anyone else who things this is useful so that they might increase the priority.

---

### Post by emddom on 2009-05-29
I'd like to try this method.
However, I don't know how to interpret the diff.
Which diff is/was used ? And can those lines be used as a script ?

Thanks,
endre


> **Brandon Williams said:**
> I finally got this working. I have a 2GB USB key set up as a persistent install with a separate 500MB partition for file storage.

Here's what I did:
[LIST=1]
[*] use fdisk to create two partitions on the usb key
[LIST]
[*] 1 1.5GB FAT16 partition (/dev/sdb1) ... the extra space is to allow enough room for a casper-rw file
[*] 1 Linux EXT partition of the remaining size (/dev/sdb2)
[/LIST]
[*] make the filesystems on the partitions
[LIST]
[*] sudo mkfs.vfat -F 16 -n unr-904 /dev/sdb1
[*] sudo mkfs.ext2 -b 4096 -L data-storage /dev/sdb2
[/LIST]
[*] mount the image and the DOS partition
[LIST]
[*] sudo mount -o loop ubuntu-9.04-netbook-remix-i386.img ./IMG
[*] sudo mount /dev/sdb1 ./DOS
[/LIST]
[*] make a copy of  /usr/share/usb-creator/install.py and modify it as per the following diff
=====================================================
79,82c79,82
<     popen(['rm', '-rf', '%s/syslinux' % target])
<     popen(['mv', '%s/isolinux' % target, '%s/syslinux' % target])
<     popen(['mv', '%s/syslinux/isolinux.cfg' % target,
<             '%s/syslinux/syslinux.cfg' % target])
---
>     #popen(['rm', '-rf', '%s/syslinux' % target])
>     #popen(['mv', '%s/isolinux' % target, '%s/syslinux' % target])
>     #popen(['mv', '%s/syslinux/isolinux.cfg' % target,
>     #        '%s/syslinux/syslinux.cfg' % target])
100c100
<                         line.insert(pos, 'cdrom-detect/try-usb=true')
---
>                         #line.insert(pos, 'cdrom-detect/try-usb=true')
=====================================================
[*] sudo install-mbr /dev/sdb1
    (this is probably not necessary, but I'm not certain)
[*] sudo syslinux -sf /dev/sdb1
[*] sudo ./install.py -s ./IMG -t ./DOS -p 256
[/LIST]

---

### Post by Brandon Williams on 2009-05-29
If you look carefully at the diff, you'll notice that it's just showing you a bunch of specific lines that should be commented out. It should be easy enough to open your copy of install.py in an editor, search for the specific lines quoted in my diff, and comment them out.

---

### Post by pdonner on 2009-07-11
Brandon,

What adjustments would I have to make to the file sizing to support the two files systems for a 32G USB?

Thanks.

---

### Post by Brandon Williams on 2009-07-11
Whether you're using a 2GB drive or a 32GB drive, the instructions should be OK for you. The method that gives you a non-persistent install wants a 1GB partition for UNR and the persistent method wants a 1.5GB partition. In both cases, the remainder of the drive can be left as one big partition or divided up, as you see fit.

---

