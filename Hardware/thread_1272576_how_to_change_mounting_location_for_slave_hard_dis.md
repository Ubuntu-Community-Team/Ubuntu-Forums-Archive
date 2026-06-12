---
title: "how to change mounting location for slave hard disc"
date: 2009-09-22
forum: Hardware
---

### Post by mimoza on 2009-09-22
I've installed new hard disc in my computer. It's the second one and it's slave.
Every time I am saving or doing smthng on it, it is shown like an external hard disc, like it is connected by usb. And it shows on desktop. And it's mounting point is "/media/" on the master hd.

I am using Ubuntu 9.04(JJ).

I want to change mounting location to just on computer "computer:///" or like just "/".

I am quite new to ubuntu and I need help with this.

Thanks in advantage.

---

### Post by scragar on 2009-09-22
Normal mount points are in /media so it shows on the desktop, or /mnt so it doesn't, unless you've got a reason it's normally accepted to stick to one of those two(For example a dedicated home partition is a legit reason).
To change the mount point you'll first need to make a new directory for it:
```
sudo mkdir **/mnt/HD2**
```
Then edit your fstab:```
sudo gedit /etc/fstab
```And change the dir it's set to mount to(try to avoid changing anything else).

---

### Post by mimoza on 2009-09-22
thanks. so now I've done it (codes in terminal), and I got new window (terminal) in which says:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=aa630a03-f2b2-443d-ace5-61145171de8e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=a36845d2-9adb-47b1-9b2f-c191257834bb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

-and now I'm even more confused. do I need to change "/dev/sda5" to /mnt/HD2" or...?

---

### Post by scragar on 2009-09-22
That's strange, your second HD isn't listed in there, it's not automounted(it must be mounting just when you go to use it from the places menu).
You can add an entry for it if you want, first post the output of:
```
sudo blkid
sudo fdisk -l
```Please.

---

### Post by mimoza on 2009-09-22
ok. I've done it. so this came out:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2b8f6d74

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18702   150223783+  83  Linux
/dev/sda2           18703       19457     6064537+   5  Extended
/dev/sda5           18703       19457     6064506   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005f7cd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

```

---

### Post by scragar on 2009-09-22
You forgot to post the block IDs for the partitions, still, it's not 100% needed.
```
sudo -i
echo "/dev/sdb1 **/mnt/HD2**         auto    relatime,errors=remount-ro 0       2">>/etc/fstab
```Run that, you won't even have to edit it :p

Then unmount and remount your second HD```
umount /dev/sdb1
mount /dev/sdb1
```

---

### Post by mimoza on 2009-09-22
I did. And I'm now on location "root@(comp.name):~#"
And... that's it?

---

### Post by scragar on 2009-09-22
That's it. It should be mounted to /mnt/HD2 which you can check by running```
mount | grep sdb1
```

While we are at it you should probably type```
edit
```on that terminal, it's currently logged in as root, not the best idea to leave it like that and forget about it because of the huge power a root user weilds.

---

### Post by mimoza on 2009-09-22
Yep. It's there. :D
Thanks so much for help. :)

---

