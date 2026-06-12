---
title: "How to Disable access to rest of the drive/partition and second HDD"
date: 2012-03-09
forum: Hardware
---

### Post by nomanfayez on 2012-03-09
I have two HDD 2TB and 200GB.

while installing Ubuntu 11.10 I remove 2TB from my PC and install Ubuntu in 200 GB HDD (*root partition* in "/dev/sdb2" and *swap* at /dev/sdb8.

Now I want the following:
 
find the screen shot. My second (2TB) HDD has lot of encrypted drives.
these are not in the computer (my computer home) list, so they are not  mounted as well. but rest of the drives are in visible and right click  mount/unmount list. I want to stop Ubuntu accessing all these drives not  even mount/unmount list and not again visible after restart (like  Ubuntu failed to read my encrypted drives... It should also failed to  read-write all my NTFS or ext3 drives).
It (Ubuntu) should only get the access to File system Drive (which is the " / " of it).

Please help me by details command.. I am a new in linux

I need to stop access my second HDD from Ubuntu 11.10 and also I want to  stop the rest of the partition rather that Ubuntu's root partition of  it.
Ubuntu should only access to its file system partiotion.

Visit here I have posted some screen shot there.. please give me an answer on it --

[http://www.linuxquestions.org/questions/ubuntu-63/how-to-disable-access-to-rest-of-the-drive-partition-and-second-hdd-932354/](http://www.linuxquestions.org/questions/ubuntu-63/how-to-disable-access-to-rest-of-the-drive-partition-and-second-hdd-932354/)

---

### Post by matt_symes on 2012-03-09
Hi

If a user has access to a terminal and has admin privileges then they can mount (and see) the drive. There is not much you can do about that.

Please post the output of

```
cat /etc/fstab
```

Kind regards

---

### Post by ahallubuntu on 2012-03-09
This might work:

[http://www.worldofnubcraft.com/969/hide-your-disks-or-partitions-from-nautilus/](http://www.worldofnubcraft.com/969/hide-your-disks-or-partitions-from-nautilus/)

This won't make it impossible to access the partitions, just remove them from the lists of possible partitions to mount.  But if they are encrypted anyway, they should be pretty secure right?

---

### Post by oldfred on 2012-03-09
You can in fstab mount them and hide. In fstab 777 means no access by anyone. noauto means it will not mount automatically.

Hide windows mount with noauto:
/dev/sda2 /Windows/sda2 ntfs defaults,noauto,umask=777 0 0

More info on how to use fstab:

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by nomanfayez on 2012-03-09
solved it...
 
 
Wish you all the best !!

---

