---
title: "usb dev loading order/mount point"
date: 2008-03-18
forum: Hardware &amp; Laptops
---

### Post by dun270 on 2008-03-18
Hello. Running dapper, 6.06 w 1TB usb
1-initally had a 60gb usb as /dev/sdc1>3, floppy was sdb
2-then added a 300gb usb as /dev/sdd1>4
3-removed both entirely, added a 1TB usb as /dev/sdf1>4
4-every reboot changes mount point from sdf to sdg, or sdg to sdf, floppy to whatever of those isn't the 1TB USB
5-floppy has never been able to mount /dev/sdb, or /dev/sdc
6-must edit fstab after every boot to mount USB drive/partions, DESPITE mtab showing mounts w correct mount points. fstab either has wrong mount points, /dev/name, or is absent of those entrys.
7-have read froum about 10-local.rules(not present in /etc/udev/rules.d), mdadm.conf(which is not present in /et/mdadm/.
8-repeat, I only have the one 1TB USB drive attacted now, and a USB floppy, have never been able to mount floppy at /dev/sdb, sdc, nor 1TB to /dev/sdc, sdd.
9-any ideas, comments. Thank You

---

### Post by Rocket2DMn on 2008-03-19
Because your entries keep changing, you should try using UUIDs in your fstab file rather than /dev locations.  There is a fancy command to show them which I have forgotten off the top of my head, but using this works just as well:
```
ls -l /dev/disk/by-uuid/
```

---

### Post by dun270 on 2008-03-23
Hello. You may have wondered my delay in "thank you";
1-partitions 1-4 mounted using UUID in the fstab
2-unmounting #3  parttion umounted all partitions
3-could not remount partition #3 although others did remount
4-had to use 'dev' in fstab to remount partition # 3
5-rebooting sends dev and mounts from sdb to sdc to sdd to sdf to sdg to sdh, etc w floppy going to a mount either one letter before or after mount of 1TB drive
6-fdisk shows inconsistent info as to fs type on partition # 3 that was unmounted

Can I delete paths, id, label, uuid, data in /dev/disk of old, and unused drive/partiton?
QParted of no use as 1TB drive shows garbled data of partitions and fs type and partiton #, and not in ordered arrangement
mtab shows true placement of dev and mount, but still fstab is inconsistent
currently using UUID for parttiton 1, 2, and 4, but dev for # 3, but using UUID for # 3 doesn't work, and orignal UUID for # 3 has been lost and replaced w 23 digit ascii id
Any more ideas?

---

### Post by Rocket2DMn on 2008-03-23
You can remove entries for old partitions, or just comment them out by placing a # in the front of the line.  You can use GParted instead of QParted by, either from the LiveCD or by downloading it into Ubuntu
```
sudo apt-get install gparted
```
System->Administration->Partition Editor
If you change a drive/partition, the UUID will probably change, too, so you will have to re-enter it into fstab appropriately.  If you need further help, post the outputs of
```
sudo fdisk -l
cat /etc/fstab
```
and specify which devices/uuids are having trouble.

---

