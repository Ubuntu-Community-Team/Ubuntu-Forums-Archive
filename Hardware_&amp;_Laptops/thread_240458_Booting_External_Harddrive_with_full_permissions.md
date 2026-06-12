---
title: "Booting External Harddrive with full permissions"
date: 2006-08-20
forum: Hardware &amp; Laptops
---

### Post by Skia_42 on 2006-08-20
I have a 40gb LaCie external Harddrive but it always boots as a read-only file system. How do I boot it with as a read/write filesystem?

---

### Post by neouser99 on 2006-08-21
is the LaCie your boot drive? or are you just plugging it in as a backup drive?

assuming it is not your boot drive - two things could be wrong. if it is an ntfs drive, there is no stable read/write, yet (its getting really really really close). or something in your /etc/fstab is forcing it to load ro, could be your user is non-admin or something along those lines.

if it is your boot drive, then it is most likely again something with your /etc/fstab setting your root partition to ro.

-neo

---

### Post by Skia_42 on 2006-08-21
I want to back up all of my data onto my external harddrive, it is not my boot drive. It is probably an ntfs driver since I originally used it with a Mac OSX computer. How do I check if its ntfs and how do I format the drive in ubuntu? I don't care about any of the data on it.

---

### Post by g_rael on 2006-08-28
gnome partition editor - "gparted"

---

### Post by suchawato on 2007-11-03
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/134712](https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/134712) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi.
I have a LaCie as well.
Couple of things here.
One: this may be related to a high priority Bug in Gutsy related to gparted.
Two, If this helps the format on a LaCie is HFS+. LaCie recomends reformating if you need to use it with both windows and Mac. Ubuntu should recognize and read HFS+ but if it were not for the aforementioned bug in Gutsy perhaps.
My LaCie worked just fine (after I changed the permissions)  until the other day (it worked just fine for about a week) when Gutsy suddenly seemed to think it was a read only drive.

---

### Post by suchawato on 2007-11-03
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnome-volume-manager/+bug/132349](https://bugs.launchpad.net/ubuntu/+source/gnome-volume-manager/+bug/132349) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Here is a duplicate bug with an ongoing comment you might want to comment on.
It is linked to the first bug.

---

