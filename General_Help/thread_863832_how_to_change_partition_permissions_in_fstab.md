---
title: "how to change partition permissions in fstab?"
date: 2008-07-18
forum: General Help
---

### Post by adredz on 2008-07-18
i have 5 partitions:/,/boot,/home,/media/Storage,and swap.i want to change the permissions of the / and /boot to root only. it kind of surprised me they weren't set to root after a fresh install. below is my fstab file:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=50b57e42-34b2-4594-880e-1c7abcf3d7c6 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=e268b82f-b4dd-4cbc-ba73-9335d5b3f7a2 /boot           ext3    relatime        0       2
# /dev/sda3
UUID=e21daf7e-dae8-4de5-a2af-15fe49fe7d14 /home           ext3    relatime        0       2
# /dev/sda5
UUID=c3f2c992-d0f2-48cd-902d-856afd36a979 /media/Storage  ext3    relatime        0       2
# /dev/sda6
UUID=afb7f4a4-09f0-4fe3-8985-587017d27e83 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


what changes should i make? 
thanks!

---

### Post by lswb on 2008-07-18
Your goal is ambiguous. What do you mean by "root permission"? I'm guessing you mean that only superuser has write permission. If you type 

  ls -ld /
  ls -ld /boot
 in a terminal I think you will find that these already look like:

drwxr-xr-x 22 root root 4096 2008-07-17 21:17 /

and

drwxr-xr-x 3 root root 4096 2008-07-16 08:18 /boot

---

### Post by adredz on 2008-07-18
sorry, yup i meant only superuser has write permission. because when i right click on all files in those partitions as a USER, i have a cut, write, and delete permissions when i shouldn't have. those options should be grayed out. i have exactly the same output from both commands. so what does that mean?

---

### Post by lswb on 2008-07-18
if your directory listings for / and /boot look start with drwxr-xr-x then it is as it should be. If not, open a terminal and type

sudo chmod ug-w /
and 
sudo chmod ug-w /boot

Note that in linux filesystems, permissions are set for individual files and directories, not for the entire partition as would be done for example when mounting a fat filesystem in fstab.

---

### Post by adredz on 2008-07-19
thanks a lot lswb!

---

