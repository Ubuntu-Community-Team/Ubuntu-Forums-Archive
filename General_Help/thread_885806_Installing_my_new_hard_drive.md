---
title: "Installing my new hard drive"
date: 2008-08-10
forum: General Help
---

### Post by Giak on 2008-08-10
I got a new hard drive, I removed NTFS from it and formated it with ext3. Now I can't write to it. How can I fix this? I am not a skilled user so I would not like lots of terminal work or changing config files by hand.

---

### Post by Sycron on 2008-08-10
Can you give more detailed information ?

---

### Post by Giak on 2008-08-10
When I mount it and try to make a folder the text is gray. If it helps, it says the permissions could not be determined.

---

### Post by Giak on 2008-08-10
Now I tried fixing it by right clicking it when it was mounted and going to properties. I set the mount option to root in the blank field and unmounted. Now it won't mount because of it, and I can't find a way to undo it. It fills in my password automatically by the way

---

### Post by Sycron on 2008-08-10
Tell me name of your hdd partition , i mean /dev/sda1/ , /dev/sdb4 , and i'll tell you haw to do it.

---

### Post by Giak on 2008-08-10
It (the drive) is /dev/sda. The partition is /dev/sda1.

---

### Post by Sycron on 2008-08-10
you can go again to properties and change mount point to /media/new_hdd

---

### Post by Giak on 2008-08-10
Where? I don't see anywhere in the properties I can.

[[IMG]http://img91.imageshack.us/img91/3672/84513165nm2.png[/IMG]](http://imageshack.us)

---

### Post by logos34 on 2008-08-10
You need to chown and chmod it:

[https://help.ubuntu.com/community/InstallingANewHardDrive#Mount%20the%20Drive](https://help.ubuntu.com/community/InstallingANewHardDrive#Mount%20the%20Drive)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
(bottom)

---

### Post by Giak on 2008-08-10
Alright, I managed to mount it again. But I have the same problem still. I cannot write to it.

Here is the log for the mounting if you want to see it.

```
hjemmeserver@hjemmeserver:~$ sudo mkdir /media/mynewdrive
sudo: unable to resolve host hjemmeserver
[sudo] password for hjemmeserver: 
hjemmeserver@hjemmeserver:~$ sudo mount /dev/hdd1 /media/mynewdrive
sudo: unable to resolve host hjemmeserver
mount: special device /dev/hdd1 does not exist
hjemmeserver@hjemmeserver:~$ sudo mount /dev/sda1 /media/mynewdrive
sudo: unable to resolve host hjemmeserver
hjemmeserver@hjemmeserver:~$ sudo mount /dev/sda1 /media/mynewdrive 
sudo: unable to resolve host hjemmeserver
mount: /dev/sda1 already mounted or /media/mynewdrive busy
mount: according to mtab, /dev/sda1 is already mounted on /media/mynewdrive
hjemmeserver@hjemmeserver:~$ 

```

---

### Post by linux_tech on 2008-08-10
what is the result of cat /etc/fstab
if you want to auto mount at boot then you should add a line

---

### Post by Giak on 2008-08-11
```
hjemmeserver@hjemmeserver:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6d6d0ae5-402d-4f51-8348-7a9032249f58 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=1e4726d6-ab6c-4d07-b60f-c76ea6994742 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
hjemmeserver@hjemmeserver:~$ 


```

---

### Post by Giak on 2008-08-14
Now it won't mount again. Any ideas?

---

