---
title: "Migrating to Ubuntu server edition from CentOS, cannot resize centos root"
date: 2008-10-22
forum: General Help
---

### Post by KNO3 on 2008-10-22
Hi,
I am currently trying to migrate from Centos5 and I need to resize its root partition (sda2).  The partition is a primary partition formatted with ext3. And centos works fine at the moment, mounting it from /dev/VolGroup00/LogVol00 (that is from /etc/fstab).

Obviously I cannot resize it within centos, so I have tried the GParted live cd, and that is unable to mount it, or manipulate it, stating that it does not recognise the format.  So i tried Knoppix, and it seems to crash QTparted.

So I tried to mount it manually with:```
mount -t ext3 /dev/sda2 /media/sda2
```and it says that I am trying to mount it with the wrong fs.  So i tried mounting it from /dev/VolGroup00/LogVol00, which it did not find.

So, my question is does anybody know of somthing funny that CentOS does to its root partitions which would cause them to be unmountable outside of the OS? or can anybody think of any reason why I am unable to mount this partition?

Thanks in advance!
kno3.

---

### Post by bodhi.zazen on 2008-10-22
Centos uses LVM and resizing a LVM is a bit harder.

See this thread (yes it is on LUKS, but it is almost the same thing really).

[How to: Resize an Encrypted Partition (LUKS) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?p=4530641")

---

### Post by KNO3 on 2008-10-22
> **bodhi.zazen said:**
> Centos uses LVM and resizing a LVM is a bit harder.

See this thread (yes it is on LUKS, but it is almost the same thing really).

[How to: Resize an Encrypted Partition (LUKS) - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?p=4530641")

thanks very much for your help!

---

### Post by bodhi.zazen on 2008-10-22
No problem. Take care re: fragmentation. The LV can fragment over the PV. If this happens, when you downsize you may lose data.

You may be best off mounting the LV and making an image of the filesystem (with dd) or copying the data off and restoring it if needed after resizing.

---

