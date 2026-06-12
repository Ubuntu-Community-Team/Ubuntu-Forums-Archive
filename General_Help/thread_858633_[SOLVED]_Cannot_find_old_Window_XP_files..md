---
title: "[SOLVED] Cannot find old Window XP files."
date: 2008-07-13
forum: General Help
---

### Post by Poptarts4liffe on 2008-07-13
Hey, I'm brand new to Ubuntu, and I was going to move all my itunes music over to Ubuntu, but i can not find any of my old Windows XP files. If I go to Places, there is Home Folder, Desktop, Documents, Music, Pictures, Videos, Computer, CD/DVD creator, Floppy Drive, Network, Connect to server,  Search for file, and Recent Documents. I looked through these and I can't find my old Windows XP files. 
Are they located somewhere else? Or did i install something wrong? 
Thanks in advance, I'm clueless.

---

### Post by CatKiller on 2008-07-13
It's possible that when you installed Ubuntu, you told it to use the entire drive, in which case the partition that held your previous Windows installation would have been destroyed.

Otherwise you would have resized your Windows [partition]("http://en.wikipedia.org/wiki/Disk_partition") to free up some space for Ubuntu. In that case, going to Computer will show that partition in addition to the Filesystem. Double-clicking on that partition will [mount]("http://en.wikipedia.org/wiki/Mount_(computing)") that partition so that you can access the files.

---

### Post by ghost_ryder35 on 2008-07-13
post the results of
```

cat /etc/fstab

```
if there is no entry for your windows partiton in this then it is likley you wrote over it...
should look something like this
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=4baf3812-9ead-4b2f-9e3f-8d70d227d969 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=45bee65f-62f7-4c78-94d9-c1dbae28c326 /boot           ext3    relatime        0       2
# /dev/sda5
UUID=da7320f9-f769-4a60-8402-c2cbf6ae7e3d /home           ext3    relatime        0       2
# /dev/sda6
UUID=850d325e-b6f7-4150-b204-a96c27add68c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```
u should see a partition that is formatted as NTFS, if you dont, well u could try some partition recovery software if what was on the windows partition was important to you.

---

### Post by Poptarts4liffe on 2008-07-13
I just loaded Windows to copy some files over, they are there. It's just i can't reach them through Ubuntu. Or I'm missing something obvious. Thanks for the help.

---

### Post by ghost_ryder35 on 2008-07-13
u should install NTFS-3G

---

### Post by Poptarts4liffe on 2008-07-13
```

bd@bd-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

---

### Post by DizzyTech on 2008-07-13
You must be using Wubi!  Since Wubi mounts your XP's drive as a system folder and not a media disk, you'll find all of your files in the /host/ folder.  You can find it under Places >> Computer.  Double-click on Filesystem and then the "host" folder.  You'll find all of your stuff there.

---

### Post by Poptarts4liffe on 2008-07-13
Omg thank you so much. There they all are :). Thanks.

---

