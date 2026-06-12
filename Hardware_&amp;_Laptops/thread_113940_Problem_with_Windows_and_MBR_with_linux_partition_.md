---
title: "Problem with Windows and MBR with linux partition table"
date: 2006-01-07
forum: Hardware &amp; Laptops
---

### Post by Laterix on 2006-01-07
I would like to install Windows XP to my computer with ubuntu, but it seems that it's not possible without removing my 250Gb partition. Here is my situation:

I have 3 Harddisks. My primary master is 250Gb harddisk with linux partition table and one ext3 partition. My second harddisk is primary slave where I would like to install windows and after that ubuntu. Windows installer says that it can't write primary masters Master boot record, because it contains linux partition table. So, is there any way to get Windows installed without removing my 250Gb partition from my primary master disk (and removing MBR with partition table)?

Here are my disks:
Primary master 250Gb (linux partition table - one ext3 250Gb partition)
Primary Slave 60Gb (Ubuntu partition and swap) <-- Can be deleted
Secondary Master 120Gb <-- shouldn't matter considering this problem

Hopefully someone can advice me. Also "You just can't do it" is a good answer if that's the case. :)

---

### Post by lha on 2006-01-07
There's no need to mess around with your 250GB drive's partition table. (Or with it's MBR.)

Do you have a reason why you would like to keep 250GB drive as primary master?

If not, I would wipe out everything on 60GB drive and make it primary master. 250GB drive would now become primary slave. Then I'd install Windows and Ubuntu on 60GB drive. Windows should install happily to a clean hd and Ubuntu will be happy too. Just remember to leave unpartitioned space when installing Windows. :p

If you do, you can make 60GB disk temporarily primary master and install Windows on it. After that swap it back to it's original place and install Ubuntu.

---

### Post by Laterix on 2006-01-07
Thanks, that's actually a good idea. No, I don't have any special reason to keep it as primary disk. If I change my 250Gb to slave it's MBR still contains Grub if I understand correctly. Does this matter somehow?

---

### Post by lha on 2006-01-09
[QUOTE=Laterix]Thanks, that's actually a good idea. No, I don't have any special reason to keep it as primary disk. If I change my 250Gb to slave it's MBR still contains Grub if I understand correctly. Does this matter somehow?[/QUOTE]

250GB drive will still have GRUB on its mbr but you don't have worry about that.

---

### Post by Laterix on 2006-01-09
Ok, now I just have to find some time to install them. Thanks a lot, I appriciate your help.

EDIT: Well, Windows didn't work on my computer so now I'm happily Kubuntu only user. :) This works just fine.

---

