---
title: "Need help mounting harddisks"
date: 2007-02-07
forum: Hardware &amp; Laptops
---

### Post by RythmDivine on 2007-02-07
Hello, me again! :)

**Situation**

I am having trouble mounting my hdds. I have made the following partritions:

hda1 15GB EXT3  this is /
hda2 175GB EXT3 not mounted atm
hdb1 200GB EXT3 this is /home
hdc1 20GB NTFS this is Audio
hdc2 20GB NTFS this is Pics
sda1 2GB EXT3 this is /swap
sda2 318GB EXT3 this is mounted as sda2 (shown on desktop as hdd)
sdb1 80GB EXT3 this is mounted as /film

**Problem**

I am not familiar enough with how to mount disks, make links etc. so i need a bit of help here on how to do it.

I want to

1) copy hdc1 and hdc2 to hda2 temporary, so i can reformat hdc to EXT3, then copy them back again.

2) i want to mount hda2, hdc1, hdc2, sda2, sda1. i want this mounting to be in a logical place, i think /media is the best place, correct? 

3) Also, i want to have shortcuts/links on the desktop to these partritions.

4) Also, i want more logical names for the partritions, sda2 should be named "Film Xvid" on the desktop etc

As you can see, i managed to reformat several drives already, and also been able to mount sdb1. However i would like to move the mountingpoint of sdb1 from /film to /media/film MPEG is this possible?

I also got an external USB hdd (FAT32?) that i want to auto-mount if it is connected at boot. 

hope you can help me, and please advice me if i am being illogical about mountingpoints.

---

### Post by DagMan on 2007-02-07
can you post the output of ```
cat /etc/fstab
```

---

### Post by housam on 2007-02-08
Read [this guide ]("http://doc.gwos.org/index.php/DapperGuide#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only")

---

