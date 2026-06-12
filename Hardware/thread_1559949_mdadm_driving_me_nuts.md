---
title: "mdadm driving me nuts"
date: 2010-08-24
forum: Hardware
---

### Post by Fafler on 2010-08-24
So, i'm working on this machine, which trashed a ext4 filesystem yesterday.  I need to make a RAID 0 array with two 1 tb drives for temporary data:

root@qnap:~# mdadm --create --verbose /dev/md1 --level=0 /dev/sde /dev/sdf
mdadm: no raid-devices specified.
root@qnap:~# 

The system is debian squeeze and i already have a RAID 5 array running with sda, sdb and sdc. It doesn't matter if /dev/md1 is present or not (mknod vs. udev). What am i doing wrong here?

---

### Post by rdwilliamson85 on 2010-08-30
mdadm --create --verbose /dev/md1 --level=0 **--raid-devices=2** /dev/sde /dev/sdf

---

### Post by Fafler on 2010-08-31
No, that didn't work either. Anyway, i worked around without the raid. Thanks anyway ;-)

---

