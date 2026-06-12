---
title: "Harddrive Ownership issues"
date: 2006-08-27
forum: Hardware &amp; Laptops
---

### Post by fiver on 2006-08-27
Ok, so I've installed Dapper on my v2000 HP Comaq Presario laptop, in tandem with windows XP. Xp is on a 10Gb NTFS partition, and Dapper is on 10Gb of Ext3, space, with the remaining 17 or so GB of the drive being partitioned off to serve as common ground for my files. This worked fine under Breezy, but Dapper seems to have a problem with it. When I try to access the other partitions through the gui if gives me the following error

> error: device /dev/hda2 is not removable

error: could not execute pmount

Now I'm not a total n00b, but this one flies clean over my head, so help?! Any assistance is gratefully appreciated.

---

### Post by Jussi Kukkonen on 2006-08-27
pmount is the program that automounts removable devices that don't have their mount options explicitly mentioned (in /etc/fstab). Generally pmount is not used with non-removable media. My guess is that you used to have a line in /etc/fstab (and things worked), and now you don't (and even pmount won't help because the drive is not a removable one).

See [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions) -- personally I'd use mount and /etc/fstab (the latter method on that page) and not pmount, but it's up to you.

---

