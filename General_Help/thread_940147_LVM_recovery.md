---
title: "LVM recovery"
date: 2008-10-06
forum: General Help
---

### Post by Zburatorul on 2008-10-06
Hello,

I would really appreciate help on recovering some data.

I have a RAID1 array under /dev/md0 composed of devices /dev/sdb and /dev/sdc. I had lvm on the raid with 3 lv, the last of which was a snapshot partition. 

My / is on /dev/sda. Recently, I reinstalled the system (Debian lenny) and reconfigured /dev/sda with lvm. 
When I booted, the system correctly determined the presence of the RAID array and even activated it. All I had to do is import /dev/md0 back into the system.

However, out of stupidity, I ran
```
sudo pvcreate -v /dev/md0
    Set up physical volume for "/dev/md0" with 488396928 available sectors
    Zeroing start of device /dev/md0
  Physical volume "/dev/md0" successfully created
```

As it says, it overwrote the start of the device, the data is has not been affected. Now I don't know how to access the LVs on /dev/md0.

Does anyone have any suggestions on how to recover the information about the lvm volumes on the disk?

I do not have the backup file of the volume group on the raid, as I just reinstalled the system over it. Otherwise I would have just followed the instructions [here.]("http://codeworks.gnomedia.com/archives/2005/general/lvm_recovery/")

Thank you in advance.

---

