---
title: "Problem with reading one of my partitions"
date: 2010-01-01
forum: Hardware
---

### Post by hbsq on 2010-01-01
Hi all,

I got a problem with one of my partitions ( with NTFS format ), actually it was working perfectly but now a days I notice that I am not able to get the free size and if I am not able to past any file in the partition ( the free space is around 10 GB )

[[IMG]http://img130.imageshack.us/img130/4822/screenshotiy.th.png[/IMG]](http://img130.imageshack.us/my.php?image=screenshotiy.png)

please you advice,

---

### Post by oldfred on 2010-01-01
Did you use windows and not shutdown normally or hibernate. NTFS partitions have a flag that windows recognizes a problem and wants to run a checkdisk on reboot. Ubuntu and gparted see the flag and will not mount the partition until it is repaired. If you mount it without the checkdisk it may cause corruption that checkdisk would fix.

If you are sure there is no problem there is a way to force mount the partition at your own risk. But you should run checkdisk from windows first.

---

### Post by hbsq on 2010-01-01
> **oldfred said:**
> Did you use windows and not shutdown normally or hibernate. NTFS partitions have a flag that windows recognizes a problem and wants to run a checkdisk on reboot. Ubuntu and gparted see the flag and will not mount the partition until it is repaired. If you mount it without the checkdisk it may cause corruption that checkdisk would fix.

If you are sure there is no problem there is a way to force mount the partition at your own risk. But you should run checkdisk from windows first.

hi, actually before I was using Ubuntu next to Vista, after that, I deleted all Vista files manually because the partition was almost full and I couldn't save my files in any other place, so I did that and used Ubntu alone. this partition was working perfectly but now, i don't know what is up, I can read from it but I can't past any new thing.

---

### Post by oldfred on 2010-01-01
That could be permissions.

How are you mounting this.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

---

### Post by hbsq on 2010-01-02
If it is a problem of permission, why was it working perfectly with me before? I think there is some problem some where

---

