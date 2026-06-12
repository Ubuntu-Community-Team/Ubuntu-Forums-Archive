---
title: "Make 2 HDD into one"
date: 2009-10-04
forum: Hardware
---

### Post by billyboy1995 on 2009-10-04
is there anyway to make 2 hard drives into one hard drive? i can use the command line or GUI.

Thanks in advance

Bill

---

### Post by oboedad55 on 2009-10-05
> **billyboy1995 said:**
> is there anyway to make 2 hard drives into one hard drive? i can use the command line or GUI.

Thanks in advance

Bill

Ehh... What do you exactly mean?

---

### Post by daturk on 2009-10-05
I would like to know this as well. Specifically I would like to span /home over 2 physical internal drives if thats possible.

Cheers

---

### Post by louieb on 2009-10-05
Only way I know to do it is use LVM (logical volume management). 
Don't use it but [https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall](https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall)

---

### Post by brettg on 2009-10-05
You can use raid 0 to create one volume out of two drives.

You will need to reformat both drives so you must backup your files first.

Warning: Dangerous commands follow, use at own risk!

First, use gparted or fdisk to create volumes on both drives of type "linux RAID"

Second, create and mount a raid volume

```
sudo mdadm --create /dev/md0 --level=0 --raid-devices=2 /dev/sdb1 /dev/sdc1

sudo mkfs -t ext3 /dev/md0

sudo mount /dev/md0 /home
```

You will have to change the above code to suit your particular system.

More info [here]("http://tuxnetworks.blogspot.com/search?q=raid")

---

### Post by billyboy1995 on 2009-10-09
what is the easyest way

---

### Post by stinger30au on 2009-10-09
> **billyboy1995 said:**
> is there anyway to make 2 hard drives into one hard drive? i can use the command line or GUI.

Thanks in advance

Bill


yep you need one of these

[IMG]http://img.directindustry.com/images_di/photo-g/electric-drill-370359.jpg[/IMG]

and some of these

[IMG]http://www.smartpine.com.au/picts/hardware.jpg[/IMG]

):P

use your imagination and im sure you can figure it out!

---

### Post by billyboy1995 on 2009-10-12
> **oboedad55 said:**
> Ehh... What do you exactly mean?
i have two hard drives installed and i would like to make the two appear to be one drive.

---

### Post by billyboy1995 on 2009-10-24
some real help would be nice...please

---

### Post by billyboy1995 on 2009-11-06
bump??

---

### Post by freackout on 2009-11-07
> **billyboy1995 said:**
> what is the easyest way

yes lvm is the easiest way ubuntu has an lvm configuration gui too, so you can alter the partitions on the fly ie while keeping your stuff intact, however you will loose all your stuff on the first initialization of installing the lvm. but its worth the effort. lvm's may be setup whilst installing systems from the start ie in there equivalent partition managers, ie take all drive/drives & install & lvm, or whatever option you choose. then any partitions you make in the lvm can be altered to suite, at whenever you need to change, but if you want to say not bother with this, you can run say pmagic 4.5 available at distrowatch.com and just resize your partitions accordingly, or go for the full lvm. (installing lvm will wipe your data, but it will give you the glue you need), pmagic will give you flexibility but not as flexible as lvm and pmagic together.

---

### Post by freackout on 2009-11-07
> **billyboy1995 said:**
> what is the easyest way

yes lvm is the easiest way ubuntu has an lvm configuration gui too, so you can alter the partitions on the fly ie while keeping your stuff intact, however you will loose all your stuff on the first initialization of installing the lvm. but its worth the effort. lvm's may be setup whilst installing systems from the start ie in there equivalent partition managers, ie take all drive & install lvm, or whatever option you choose. then any partitions you make in the lvm can be altered to suite, at whenever you need to change, but if you want to say not bother with this, you can run say pmagic 4.5 available at distrowatch.com and just resize your partitions accordingly, or go for the full lvm. (installing lvm will wipe your data, but it will give you the glue you need), pmagic will give you flexibility but not as flexible as lvm and pmagic together. you can also complicate the process by making a volume(2 drives as one) and adding a third drive to a raid array, ((ie 2*40gb=80gb volume)+(one single 80gb)to give you a raid)

---

