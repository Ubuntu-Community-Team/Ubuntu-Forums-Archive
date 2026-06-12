---
title: "Cannot write to new EXT3 Partition"
date: 2008-07-24
forum: General Help
---

### Post by Proto_ on 2008-07-24
Hello all

I am quite a ubuntu beginner, and i need some help.

Until this morning, i was dual-booting windows and Hardy. Today, i decided to get rid of Windows (finally found how i could do everything that i wanted on Ubuntu). Installed and ran Gparted, deleted the NTFS partition and substituted it by an EXT3 Partition.

Problem is: the partition only opens as Read-Only. I cannot write to it whatsoever unless i use a Sudo (and lets face it: SUDOing evertime you need to copy a file is quite a pain.)

How do i solve/workaround this?

Thank you very much,

Proto

---

### Post by Potatoj316 on 2008-07-24
you could use gparted to merge the partitons.  Actually I think its just delete the second partition and expand the other one to fill the space.

---

### Post by Proto_ on 2008-07-24
I though of that, but, for backup reasons, I would like to keep them in separate partitions.

But thank you very much:)

---

### Post by argail1980 on 2008-07-24
maybe ubuntu still tries to mount that partition as before and that might be write-protected.
open the file ```
/etc/fstab 
```and post it's contents please

---

### Post by Archmage on 2008-07-24
You need to mount it the right way so that user can write on it. If you are the only user you could use example in /etc/fstab:

```
/dev/hdb2 /media/hdb2 ext3 rw,users,exec,uid=argail1980 0 0
```

Instead of argail1980 use your username.

---

### Post by Proto_ on 2008-07-24
Achmage:

I tried that, to no result. What i got was:

> proto@protonote:~$ /dev/sda1 /media/sda1 ext3 rw,users,exec,uid=proto 0 0
bash: /dev/sda1: Permission denied
proto@protonote:~$ sudo /dev/sda1 /media/sda1 ext3 rw,users,exec,uid=proto 0 0
sudo: /dev/sda1: command not found




argail1980:
Here is the result of gedit /etc/fstab:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=424be538-6b90-4ef4-8c04-82de66352dfe /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=88ce7070-5e6c-4b8c-95cd-7cfd05a72286 /home           ext3    relatime        0       2
# /dev/sda4
UUID=b4edea8f-38f7-4335-ba6f-2ee088ff2710 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


And Thank you very much

---

### Post by argail1980 on 2008-07-24
looks like it is not mounted automatically at all. which device was it again? and what did you do to get access via sudo?

btw: the code from Archmage was meant to be inserted at the end of /etc/fstab, not the terminal directly

Generally, this file /etc/fstab contains a list of file systems that are mounted automatically, like / and /home in ur case. Additional file systems that are not in there can only be mounted by root. Therefor you have to "register" the new partition there.

thinkin about it, it should be the device /dev/sda1 for you. then the code line from Archmage at the end of your /etc/fstab and a reboot should do the trick

---

### Post by Proto_ on 2008-07-24
The device appears as a "53.7 GB Media" in "places" menu. Opening it takes me to /media/disk. All I did to get there was a sudo nautilus and navigated there.

EDIT:
I shall try the line now and tell the results. Thank you very much

---

### Post by silkstone on 2008-07-24
When you format as Ext3 with Gparted, it makes root the owner of the partition.

Assuming that the correct partition is /dev/sda1...

```
sudo chown proto:proto /dev/sda1
```

(That changes the owner and group to proto.)

EDIT/ If you want to change the ownership of all folders and files within the partition, you use the -R switch...

```
sudo chown -R proto:proto /dev/sda1
```

---

### Post by Proto_ on 2008-07-24
Thank you all for the help, really.

But no success yet.

my new /etc/fstab is:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=424be538-6b90-4ef4-8c04-82de66352dfe /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=88ce7070-5e6c-4b8c-95cd-7cfd05a72286 /home           ext3    relatime        0       2
# /dev/sda4
UUID=b4edea8f-38f7-4335-ba6f-2ee088ff2710 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/sda1
/dev/sda1 /media/sda1 ext3 rw,users,exec,uid=proto 0 0

and i did the chow
Yet, all I get when rebooting an trying to open the same drive in the "places" menu is [IMG]http://img440.imageshack.us/my.php?image=screenshotgnomemountel8.png][img=http://img440.imageshack.us/img440/5454/screenshotgnomemountel8.th.png[/IMG]

I must be doing something wrong.

Thanks again and sorry for the n00b

---

### Post by argail1980 on 2008-07-24
silkstone: I think there should be no files on that partition yet. anyway, if it's mounted with the wrong 'umask=' then a chown will solve the problem. But I don't know if that option was only for ntfs systems.

BTW, where does ubuntu get that "53.7 GB Media" if it's not in the fstab?

---

### Post by Proto_ on 2008-07-24
The image did not work last time

[http://img440.imageshack.us/img440/5454/screenshotgnomemountel8.png](http://img440.imageshack.us/img440/5454/screenshotgnomemountel8.png)
[IMG]http://img440.imageshack.us/img440/5454/screenshotgnomemountel8.png[/IMG]

---

### Post by plucky on 2008-07-24
Try using this tutorial on the Psychocats website for [Mounting Linux Partitions](http://www.psychocats.net/ubuntu/mountlinux)

The complete website is in my **signature**

Good Luck

---

### Post by Proto_ on 2008-07-24
plucky, argail1980, Potatoj316, Archmage, my deepest thank to you all.

I can now mount and use the partition, and goodbye to windows.

Thank you very much

---

