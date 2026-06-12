---
title: "Cloning Ubuntu Installation - Will This Work?"
date: 2009-08-30
forum: Installation &amp; Upgrades
---

### Post by chriswall20 on 2009-08-30
Hi, I have been reading posts regarding cloning the ubuntu 9.04 installation to another partition or drive and whilst I understand the processes shown they seem rather complicated to me.

Anyway I had this idea of a shortcut, could anyone comment on whether it should work or not?

My idea is this; 
Unplug existing boot hard drive. 
Create clean partition on destination drive and put fresh install of ubuntu 9.04 on it using live cd
re-connect old boot drive as slave instead of master
boot live cd and copy contents of old boot partition to new drive boot partition. using cp -a command.

As I see it; being the same pc with the same components, this should give all applications and settings from original installation to the new clean installation.

Any comments whether this may work? I think it would be good if it did as it does not involve any risk to the original drive and installation.:confused:

---

### Post by DFlame on 2009-08-30
Why go through so much trouble? There is a far, far easier way.

With a [Clonezilla](http://clonezilla.org/) CD, you can just have your second hard disk as a slave, boot from the CD, and have it copy your first hard drive to the second, bit for bit. As long as your second hard disk is the same or bigger than the first, you'll have no trouble at all.

Drop another post if you need further help using the CD. I use it myself to make regular backups of my system.

---

### Post by lswb on 2009-08-30
Doing the clean install on the new disk will take care of getting a working boot loader. so that idea is OK.

One problem is that partitions are mounted in /etc/fstab by uuid. Also in /boot/grub/menu.lst, there are several places using uuid also; Check you existing menu.lst to see them.

Another somewhat obscure use of uuid is in the initrd. In /etc/initramfs-tools/conf.d there is a file named "resume" that has a line something like 
"RESUME=UUID=uuidstring-goes-here" 
The uuid there is normally for the swap partition which is used when hibernating the system. Having it wrong will cause a long delay booting and cause usplash to quit prematurely.

So, there are at least 2 approaches to fixing these problems: One is to use tune2fs or other command to change uuids of the new / and swap partitions to the same as the old disk; This is quick but will cause problems if trying to mount both old and new partitions at the same time.

The other way would to be manually edit menu.lst and fstab, and after booting the first time, edit the /etc/initramfs-tools/conf.d/resume file, then rebuild the intrd with update-initramfs or mkinitramfs.

I may (likely?) be missing some other considerations as well, hopefully others will jump in here with some experience.

---

### Post by earthpigg on 2009-08-30
[http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)

---

### Post by VMC on 2009-08-30
Some very Good reply's. In fact I use to use Clonezilla all the time, now I just use partclone.ext4 by itself ( I use ext4 file system). You need to know what your doing though. Clonezilla has some checks to help.

Now I use gparted to just copy from one partition to another, for safe keeping.

lswb brings up some good info. To further expand the resume feature do this:

```
sudo blkid
``` to get you swap id. If it is different than the one in "/etc/initramfs-tools/conf.d/resume" then simply change to value to reflect the correct id, then do:
```
sudo update-initramfs -u
```

---

