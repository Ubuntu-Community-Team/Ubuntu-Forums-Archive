---
title: "Cant mount volume problem"
date: 2008-05-28
forum: Hardware
---

### Post by chilipeppersman on 2008-05-28
i have been having a problem with my hard drive(external and internal) because when i go to open either of them i get this:(also in attachment) "Cannot mount  volume. unable to mount volume" i dont know what happened or how to fix it so would somebody help me out?
tuna

---

### Post by didac on 2008-05-29
Click the tab "Details" and post the result. Also, open a terminal and post the result of

```
cat /etc/fstab
sudo fdisk -l
dmesg | tail
```

after you plug your hard disk.

---

### Post by chilipeppersman on 2008-05-29
details that you asked: 
tuna@TheLastStand:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=2377c322-4e20-4d60-af01-749b678de105 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=6ee537bc-53ec-41ac-b08e-3aa0067417fa none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
tuna@TheLastStand:~$ sudo fdisk -l
[sudo] password for tuna: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7d7d7d7d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       28969   232693461    7  HPFS/NTFS
/dev/sda2           28970       38913    79875180    5  Extended
/dev/sda5           28970       38502    76573791   83  Linux
/dev/sda6           38503       38913     3301326   82  Linux swap / Solaris
tuna@TheLastStand:~$ 

hope this helps

---

### Post by didac on 2008-05-30
Your Windows hard disk has been marked as dirty and it cannot be mounted unless you reboot to Windows and allow Windows to do a disk check.

Another solution -- not recommended, just in case you despair -- is to type in a terminal:

```
sudo mount /dev/sda1 /media/disk -o force
```

---

### Post by chilipeppersman on 2008-05-30
so should i just go into windows and have do a disk clean/check or will it do it automatically? also, should i just get a new harddrive, because i have been having problems in windows also. and what does that terminal entry do and why would i have to be in dispair to do it?

---

### Post by chilipeppersman on 2008-05-31
well i got it to mount my internal hard drive, but when i try to get it to read my external i get the same thing that i would usually get with my internal, and i included the message i get in my attachement. i really need to know pretty soon about my hard drive, that is if i need to get a new one. because i am building a new pc soon, and i dont want a bad hard drive. so if anyone could please tell me that as soon as you can that would be great.

---

### Post by gummygod on 2008-06-01
ive gotten that message before and i just did

```
sudo mount -t ntfs-3g /dev/sdb1 /media/whatever -o force
```

then i always clicked unmount before turning it off and that did the trick.  altho once i upgraded to 8.04 ive been having more problems. im not sure how to edit fstab and i get this error: Unprivileged user can not mount NTFS block devices using the external FUSE ...

so i hope that helps you chilipeppersman, and anyone know what my prolem is?

---

### Post by chilipeppersman on 2008-06-01
thanks for the input gummygod, but im stopping using ubuntu and going back to windows... it was messing with my system, and i didnt need it, even though i found out that threatfire was the problem on my windows machine...

---

