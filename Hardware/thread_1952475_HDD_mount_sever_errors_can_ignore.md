---
title: "HDD mount sever errors can ignore"
date: 2012-04-04
forum: Hardware
---

### Post by S.nazari on 2012-04-04
I have a HHD 1TB Hitachi SATA. None Raid. 
NTFS
One partition all NTFS.
Contents are all my data. 

I have setup fstab to mount it. 
Here is what I have done. 


```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb3 during installation
UUID=28b7b566-78de-438a-9481-ac1f8478ad7f /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdc3 during installation
UUID=14039DE425ECED41	/media/sorush4Disk1	ntfs	defaults	0	2
# swap was on /dev/sdb2 during installation
UUID=6478adf6-6b80-4317-aba2-5755dd9b939b none            swap    sw              0       0
/dev/fd0u1440        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

UUID=cbf4aa35-7d86-45f5-9c6e-0cbe31e2c85a	/home	ext4	defaults	0	2

```

I don't know why I keep getting errors.
Check disk with chkdsk d: /F /R Finds no errors.

I am able to ignore the errors at boot up and access the partition. But I'm worried that might lead to damage of the hdd.

SMART status is fine too.
What can I do?

ntfsfix works fine without errors.

---

### Post by 2F4U on 2012-04-04
I may have overread that but what errors do you get?

---

### Post by S.nazari on 2012-04-05
I don't know what errors I get. How do I check?

---

