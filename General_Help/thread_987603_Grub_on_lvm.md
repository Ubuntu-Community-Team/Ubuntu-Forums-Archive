---
title: "Grub on lvm"
date: 2008-11-19
forum: General Help
---

### Post by jnw222 on 2008-11-19
while experimenting, i installed ubuntu 8.04 in a LVM setup, but i had no option for installing grub, and i panicked

i need grub installed and able to boot into LVM partitions

---

### Post by jnw222 on 2008-11-21
help?

---

### Post by bodhi.zazen on 2008-11-21
If you are using GRUB you need a separate /boot partition, outside of any LVM or encryption.

---

### Post by jnw222 on 2008-11-21
sda1 prepared

---

### Post by jnw222 on 2008-11-22
help?

---

### Post by bodhi.zazen on 2008-11-22
The easiest way to install Ubuntu into LVM is to use the alternate CD. use sda1 as /boot

Otherwise , where are you at exactly ? What have you done ?

[https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall](https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall)

---

### Post by jnw222 on 2008-11-22
three partitions 
sda1 plan to use as boot
sda2 data share
sda3 LVM
     ubuntu 8.04 Lts
     swap
     data

---

### Post by wanfahmi on 2008-12-04
There is a great tut at gentoo website

[http://www.gentoo.org/doc/en/lvm2.xml](http://www.gentoo.org/doc/en/lvm2.xml)

I Partitioned mine like this

sda1 Windows 60G
sda2 /boot 500mb (overkill!)
sda3 Extended
  sda5 swap 1G
  sda6 LVM 60G
      LVM / (Ubuntu root 5G)
      LVM /home (10G)
      LVM /root-gentoo (Gentoo root) 5G
      (LVM Freespace for future expansion)
  sda7 Truecrypt 10G
sda4 Data 100G

You NEED to use fdisk. GParted don't do LVM. You should put /boot on a normal partition. Start out with small LVM logical partitions. It's easier to grow a partition than shrink.

I did this using Live CD
Step 1 Partition the main partitions (sda1 thru sda4) (This part you can use GParted)
Step 2 Install Windows
Step 3 Ubuntu LiveCD again. Create the rest of the partition. Make sure /dev/sda6 get the LVM type (8e if memory serves me right)
Step 4 get lvm2 package
Step 5 modprobe dm-mod
Step 6 pvcreate /dev/sda6 (This is to prepare the "Physical Volume")
Step 7 vgcreate <pv_name> <device> (Create the "Physical Volume")
 eg: vgcreate lvmvolume /dev/sda6
Step 8 lvcreate -L 5G -n root  lvmvolume (Create a logical volume with the lable root in the physica volume named lvmvolume)
Step 9 lvcreate -L 10G -n home  lvmvolume 
Step 10 create the rest logical volume.
Step 11 Create the filesystems. mkfs.ext3 /dev/<pv_name>/<lv_name>
 eg mkfs.ext3 /dev/lvmvolume/root

Then you can install Ubuntu normally. At the partition step, select manual. Then assign the appropriate volumes.
eg:
/   set to /dev/lvmvolume/root
/boot set to /dev/sda2
/home   set to /dev/lvmvolume/home
... an the rest...

That's all you need to do. Ubuntu takes care of the rest.

Later, install system-config-lvm using this tutorial. IMO Its a better LVM manager. 
[http://ubuntuforums.org/showthread.php?t=216117](http://ubuntuforums.org/showthread.php?t=216117)

Good Luck.. (I'm still struggling on Gentoo...)

---

