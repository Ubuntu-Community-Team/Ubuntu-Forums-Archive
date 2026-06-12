---
title: "mdadm RAID 1 mount: special device ... does not exist"
date: 2009-10-20
forum: Installation &amp; Upgrades
---

### Post by snuffy47 on 2009-10-20
Hello

I have installed Ubuntu Server and was creating a RAID 1 with 2 TG drives for storage.

The tutorial I am using is [http://blog.mansonthomas.com/2009/08/add-2-disk-for-raid-1-setup.html](http://blog.mansonthomas.com/2009/08/add-2-disk-for-raid-1-setup.html).

At the step to check and see if it will unmount and mount again  using these commands  I get 
 /mnt$ sudo mount -a
mount: special device /dev/disk/by-uuid/eb6bf63b:0d49fbbc:971b34ee:0fa0ad does not exist

Now we will check that it's correct :
unmount /dev/md4 first :

cd /mnt
sudo umount /dev/md4

then try to remount all partition defined in /etc/fstab :
thomas@dev:/mnt$ sudo mount -a  check if it's mounted :

Please help

---

