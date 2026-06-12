---
title: "hdd names keep changing so mounting points mess up"
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by Tobywuk on 2009-03-13
Hello,

I recently added 2 additional internal hard drives to my ubuntu machine, one for storage and the other for backup. Each hard drive is formatted with one single ext3 partition.

In my /etc/fstab i have added the following entries to automatically mount the drives at startup. (we are assuming the original hard drive with the OS on it is sda1, storage is sdb1 and backup sdc1.)

```

/dev/sdb1 /home/user/storage ext 0 0
/dev/sdc1 /home/user/backup

```

The problem im having is that when i restart my system the reference names to these drives (eg sdb1) change and switch round making the drives mount to the wrong mount point or not mounting at all. eg.. currently my backup hdd is mounted at /home/user/storage as it currently has the name sdb1 (instead of sdc1) and the storage hard drive is not mounted at all as its now names sda1 not sdb1.

How can i set is so each of these hard drives have static non changing reference names or is there nay other way to fix my problem?

thank you.

---

### Post by taurus on 2009-03-13
Instead of using /dev/sdb1, use the UUID in /etc/fstab.

```
sudo blkid
```
And by the way, the entries for those two drives "look" funny.

```
UUID=8uw112129sncaousre139aiss  /home/user/storage   ext3   defaults   0   0
```

---

### Post by Tobywuk on 2009-03-13
Thanks for the reply. I have done what you said and it seems to be working :)

thanks for the help :)

---

