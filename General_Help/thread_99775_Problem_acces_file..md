---
title: "Problem acces file."
date: 2005-12-06
forum: General Help
---

### Post by sweetthdevil on 2005-12-06
Hi. i try to open the file /etc/mplayerplug-in.conf to modify the file to be able to read video from the net.

But i got this error :confused: 
```
sweetth@ubuntu:~$ sudo kwrite /etc/mplayerplug-in.conf
Error: "/var/tmp/kdecache-sweetth" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
Error: "/tmp/kde-sweetth" is owned by uid 1000 instead of uid 0.
```
I try to change the right by:
```
sweetth@ubuntu:~$ sudo chown root /etc/mplayerplug-in.conf
```

But i still got the same problem after that :( 

And i've got two partition in fat32 and i don't have the right to write on it..

How can i do???

---

### Post by GoldBuggie on 2005-12-06
instead of sudo write kdesu which is used when accesing graphical programs. There are numerous posts on how to fix it for sudo if you want to.

write access to your fat32 partition is possible if you change your mount settings in /etc/fstab (you can paste this file here if you want help)

I think a valid line should look something like
/dev/hdg1 /media/hdg1 vfat umask=000,uid=1000,gid=100,**exec,rw,users** 0 0

just make sure your line has the exec,rw,users option.

---

### Post by sweetthdevil on 2005-12-06
```
sweetth@ubuntu:~$ sudo kdesu /etc/mplayerplug-in.conf
Password:
sh: /etc/mplayerplug-in.conf: Permission non accordée
```

It means i don'thave permision :confused:

---

### Post by sweetthdevil on 2005-12-06
And there is my /etc/fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda8       /home           ext3    defaults        0       2
/dev/sda1       /media/sda1     ntfs    defaults        0       0
/dev/sda5       /media/sda7     vfat    defaults        0       0
/dev/sda6       /media/sda8     vfat    defaults        0       0
/dev/sda9       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

Thanks :smile:

---

### Post by GoldBuggie on 2005-12-06
Ok..first of let me say I'm sorry for beeing a bit unclear about kdesu. What you want to write is ```
kdesu kwrite /etc/mplayerplug-in.conf
```.
*kdesu* is what you want to use when starting applications like kwrite. But when executing commands on the prompt that only does a copy or move then you will use *sudo*.

Now about */etc/fstab*. From what I can see your fat32 disks are the */dev/sda5* & */dev/sda6*. So what you want to do is change those to lines. Do the following:
```
kdesu kwrite /etc/fstab
``` Then change the 2 lines to
```
/dev/sda5 /media/sda7 vfat rw,users,exec,umask=000 0 0
/dev/sda6 /media/sda8 vfat rw,users,exec,umask=000 0 0
``` 
 Then to remount the system without rebooting you can do a```
sudo mount -a
```[I](Note that here I'm using sudo since mount is not a gui written program)

[/I]Hope this helps. Let me know if you come across any questions or difficulties.

---

