---
title: "Re-partitioning"
date: 2006-05-11
forum: Hardware &amp; Laptops
---

### Post by nolongerlivecd on 2006-05-11
How do I merge 2 partitions using gparted?

I currently have 3 partitions:
hda1 - FAT32, Windows XP HOME
hda2 - ext3, Ubuntu 5.10 Breezy Badger
hda3 - ext3, Storage

I want to merge hda2 and hda3, into the hda2 entity, as I have just found out how to mount FAT32 as read-writeable, so as to expand the hda2 size... running out of space for my programs...

---

### Post by nolongerlivecd on 2006-05-12
I really need help, I have less than 100MB left in hda2, where / is mounted. I want to merge it with hda3, but Partition Magic does not allow it.

---

### Post by xyz on 2006-05-12
Hi-
Check this out:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
Great,pretty clear guides to resizing,dualboot,repartionning and so on.
Hope this helps.Good luck!

---

### Post by nolongerlivecd on 2006-05-12
It's not exactly what I'm looking for, you see. What I have, after some readjustments last night ( +8 GMT ), I have:

hda1 - FAT32, humongous waste of space, Windows
hda2 - ext3, Ubuntu 5.10 Breezy Badger.

What I want to do is to resize both, enlarge hda2 and shrink hda1

---

### Post by aysiu on 2006-05-12
[QUOTE=nolongerlivecd]It's not exactly what I'm looking for, you see. What I have, after some readjustments last night ( +8 GMT ), I have:

hda1 - FAT32, humongous waste of space, Windows
hda2 - ext3, Ubuntu 5.10 Breezy Badger.

What I want to do is to resize both, enlarge hda2 and shrink hda1[/QUOTE] You can add to the *end* of a partition to make it larger, but you cannot add to the *beginning* of a partition. You can create another storage partition, though...

---

### Post by nolongerlivecd on 2006-05-13
But would it be possible for me to install stuff on the storage partition?

---

### Post by aysiu on 2006-05-13
[QUOTE=nolongerlivecd]But would it be possible for me to install stuff on the storage partition?[/QUOTE] Hm.

You might be able to create a separate /usr partition there, but that can be tricky. You would have to move your /usr stuff over there, edit your /etc/fstab appropriately, and then delete your old /usr folder.

That's generally what the procedure is. I'm not sure of the specifics, so I don't want to give you bad directions.

---

### Post by nolongerlivecd on 2006-05-13
Right now, after using GParted livecd to expand my Windows partition, I am facing a problem.

I booted once, then tried to run a program (it was hibernated), then it gave me an exception. So, I restarted, and funny sounds started coming out of the speakers for a while, about 1 or 2 seconds. Then, now, when I try to boot into Windows, I get a weird exception, and when I reboot, during the shutting down process, I read hda1 filesystem panic.

---

### Post by nolongerlivecd on 2006-05-13
Right now, My Documents and Settings folder among others, has morphed into some other item...

[IMG]http://img143.imageshack.us/my.php?image=screenshot3dc.png[/IMG]

How do I convert it back into a folder?

---

