---
title: "external drive sometimes registers as sda1, othertimes sdc1 [esata]"
date: 2008-08-17
forum: General Help
---

### Post by blackbinary on 2008-08-17
I have a terrabyte e-sata drive, which i like to mount at /external.
It is on before i boot, and when I get into ubuntu and use 'sudo fdisk -l' It will appear as sda1 or other times sdc1. The problem is, I have a windows drive, and if the external is sda1, that means windows is sdc1. So if In fstab I added something to automount sdc1, windows will get mounted some of the time. Which really isn't what I want. Thus there must be some miscommunication going on. What can I do or edit to get this working properly?

---

### Post by louieb on 2008-08-17
Get a copy of the latest GParted. I use the one on the  [SystemRescueCd]("http://www.sysresccd.org/Main_Page").
You can right click on the partition and give it a label. then Ubuntu will mount under /media/<label>.  
Haven't done it but I belive you can use the label in fstab to tell it to mount the partition on the external somewhere else.

BTW: the label feature is new with GParted 3.7. GParted in the repositories is V3.5 so you will need to get it on a live CD.

---

### Post by drs305 on 2008-08-17
If these are ntfs or ext formatted partitions, you can label them via terminal. They should then mount on /media/*labelname* if there isn't an fstab entry.

Install labeling apps:
```
sudo aptitude install ntfsprogs
```

For ext2/3:
```
sudo tune2fs -L <label> <device>  # sudo tune2fs -L mylabel /dev/sda1
```

For ntfs:
```
sudo ntfslabel <device> <label>   # sudo ntfslabel /dev/sda2 mylabel
```

---

