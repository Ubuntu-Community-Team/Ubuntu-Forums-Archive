---
title: "[SOLVED] Local discs mounting"
date: 2008-09-13
forum: General Help
---

### Post by Nabanna on 2008-09-13
Hi,

i recently installed Ubuntu 8.04 on my computer, i previously had Ubuntu 7.10.
As in 7.10, all local discs(windows partitions) were shown on Desktop, but in 8.04 i have to go to PLACES and then click on the individual partitions to make them appear on Desktop and mount them, and that too each time i start my computer...
Is there any way they can be shown on Desktop like it was in 7.10..???
kindly help...

---

### Post by icheyne on 2008-09-13
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by Nabanna on 2008-09-13
> **icheyne said:**
> [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

Thanks...

but i am a newbie..
the document in the link you provided has too many commands(that literally goes over my head,, sorry :( )..
please tell me which command i need to use, i want the partitions to be shown on desktop without  mounting every time....
please help...

kind regards-
Nabanna

---

### Post by Nabanna on 2008-09-13
ok,

run the script as described as first method, but it only mounts it for "Read Only"...???
can the change be reverted??
is there any other method for mounting the partitions with full access?

---

### Post by WRDN on 2008-09-13
To automatically mount the disk at bootup, you need to edit the fstab file. First, open the Terminal and type:

```
sudo fdisk -l
```

This will allow you to identify the devices, which will have the format /dev/sdaN or /dev/hdaN (where N represents the partition number). The 3rd letter (a) represents the disk- a is disk one, b would be disk two, c would be disk three and so on.
Now you have found the device, create the mount point for the partition:

```
sudo mkdir /media/files
```

You can replace "files" with something else if you wish.

If you wish to mount the disk now, type:

```
sudo mount /dev/[device] /media/files
```

Otherwise, edit the fstab file by typing:

```
gksudo gedit /etc/fstab
```

Add the line:

> /dev/[device] /media/files ext3 defaults 0 0

Replace [device] with the actual device, and you may need to replace "ext3". For example, if it's a NTFS partition, replace it with ntfs.

Finally save the file. When you reboot, the disk should automatically be mounted.

---

### Post by bodhi.zazen on 2008-09-13
Rebooting is soooo old school (windows).

Just :```
sudo mount -a
```

---

### Post by WRDN on 2008-09-13
Clever clogs :D

---

### Post by Nabanna on 2008-09-14
thank you....

is there something i can do during while installation to mount the windows partitions..

i downloaded the script, but it didn't mounted the main Windows partition and that also read only..!!!(other partitions were mounted though)..

can 'NTFS-config' help me in this...  ????
(i really miss :( the way it was mounted automatically in Gusty Gibbon and shown on the Desktop) 

(i prefer to keep music, pictures & documents in Windows partitions so that they can be accessed by both Windows & Ubuntu, thus when the partitions are not mounted i have to, for example, make play list everytime i start the computer.)


regards-
nabanna

---

### Post by bodhi.zazen on 2008-09-14
> **Nabanna said:**
> thank you....

is there something i can do during while installation to mount the windows partitions..

i downloaded the script, but it didn't mounted the main Windows partition and that also read only..!!!(other partitions were mounted though)..

can 'NTFS-config' help me in this...  ????
(i really miss :( the way it was mounted automatically in Gusty Gibbon and shown on the Desktop) 

(i prefer to keep music, pictures & documents in Windows partitions so that they can be accessed by both Windows & Ubuntu, thus when the partitions are not mounted i have to, for example, make play list everytime i start the computer.)

regards-
nabanna


During the installation there is a screen to add in additional partitions.

I think you select manual configuration  and add in a mount point. Take great care NOT TO FORMAT your windows partition.

---

### Post by Nabanna on 2008-09-14
> **bodhi.zazen said:**
> During the installation there is a screen to add in additional partitions.

I think you select manual configuration  and add in a mount point. Take great care NOT TO FORMAT your windows partition.

thanks,

you mean i have to do Manual Partitioning then EDIT Partition and then add /windows as mount point and select use as ntfs to windows partitions.
(Will this make them to appear on Desktop with read+write rights???)


how can i prevent them to Format????

> **WRDN said:**
> To automatically mount the disk at bootup, you need to edit the fstab file. First, open the Terminal and type:

```
sudo fdisk -l
```

This will allow you to identify the devices, which will have the format /dev/sdaN or /dev/hdaN (where N represents the partition number). The 3rd letter (a) represents the disk- a is disk one, b would be disk two, c would be disk three and so on.
Now you have found the device, create the mount point for the partition:

```
sudo mkdir /media/files
```

You can replace "files" with something else if you wish.

If you wish to mount the disk now, type:

```
sudo mount /dev/[device] /media/files
```

Otherwise, edit the fstab file by typing:

```
gksudo gedit /etc/fstab
```

Add the line:



Replace [device] with the actual device, and you may need to replace "ext3". For example, if it's a NTFS partition, replace it with ntfs.

Finally save the file. When you reboot, the disk should automatically be mounted.

i still cannot access recent documents something like "not found...." appears....

---

### Post by Nabanna on 2008-09-14
> **WRDN said:**
> To automatically mount the disk at bootup, you need to edit the fstab file. First, open the Terminal and type:

```
sudo fdisk -l
```

This will allow you to identify the devices, which will have the format /dev/sdaN or /dev/hdaN (where N represents the partition number). The 3rd letter (a) represents the disk- a is disk one, b would be disk two, c would be disk three and so on.
Now you have found the device, create the mount point for the partition:

```
sudo mkdir /media/files
```

You can replace "files" with something else if you wish.

If you wish to mount the disk now, type:

```
sudo mount /dev/[device] /media/files
```

Otherwise, edit the fstab file by typing:

```
gksudo gedit /etc/fstab
```

Add the line:



Replace [device] with the actual device, and you may need to replace "ext3". For example, if it's a NTFS partition, replace it with ntfs.

Finally save the file. When you reboot, the disk should automatically be mounted.

Kindly help me .....
i tried the above method(used c,d,e....) + NTFS Config(using C,D,E).....
now the 'media'  shows c, C, d, D, e, E.....
please help me out in removing c,d,e.. from it without data loss...
(i apologize, i am a total newbie and noob)

---

### Post by Nabanna on 2008-09-15
any suggestions please.......

---

### Post by bodhi.zazen on 2008-09-15
> **Nabanna said:**
> any suggestions please.......

I can not understand what your problem is exactly and what you are doing.

The terms c/d/e is how windows refers to partitions and is meaningless in Linux. You might as well use terms like ^ % !

See : [HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=282018")

Second, what is it you want to do ? Mount ntfs partitions ? 

Show us the contents of /etc/fstab and the output of "ls /media" and "sudo fdisk -l".

See also: 

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by Nabanna on 2008-09-17
> **bodhi.zazen said:**
> 

Show us the contents of /etc/fstab and the output of "ls /media" and "sudo fdisk -l".



Hi bodhi.zazen, 
thanks for replying, and sorry for my late reply.
heres what you asked......

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0e842e7a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5222    41945683+   7  HPFS/NTFS
/dev/sda2            5223       38913   270622957+   f  W95 Ext'd (LBA)
/dev/sda5            5223       10444    41945683+   7  HPFS/NTFS
/dev/sda6           10445       16971    52428096    7  HPFS/NTFS
/dev/sda7           16972       23498    52428096    7  HPFS/NTFS
/dev/sda8           23499       31205    61906446    7  HPFS/NTFS
/dev/sda9           31206       31329      995998+  82  Linux swap / Solaris
/dev/sda10          31330       34441    24997108+  83  Linux
/dev/sda11          34442       38913    35921308+  83  Linux

please see the attached image, it might help you to understand my problem, please note uppercase and lowercase c, d, e ....etc.
The folders with uppercase was created by NTFS-Config(which i removed later) and which contains the data

 and 

lowercase named folders were created by method using-

sudo mkdir /media/files
sudo mount /dev/[device] /media/files

and these folders are empty.
So i want to remove the folders which are empty (ie c, d, e....) without messing or losing actual data.


regards..

---

### Post by russlar on 2008-09-17
> **Nabanna said:**
> Hi bodhi.zazen, 
and these folders are empty.
So i want to remove the folders which are empty (ie c, d, e....) without messing or losing actual data.


regards..

if the folders are empty, and there isn't a drive mounted on those directories, you should be able to run sudo rmdir {insert name here} to remove the emtpy directories.

---

### Post by bodhi.zazen on 2008-09-17
To see what is mounted where, :

```
mount
```

To remove an empty directory ( c ):

```
rm -rf /media/c
```

So long as the directory is empty there will be no data loss.

---

### Post by Nabanna on 2008-09-18
> **russlar said:**
> if the folders are empty, and there isn't a drive mounted on those directories, you should be able to run sudo rmdir {insert name here} to remove the emtpy directories.

> **bodhi.zazen said:**
> To see what is mounted where, :

```
mount
```

To remove an empty directory ( c ):

```
rm -rf /media/c
```

So long as the directory is empty there will be no data loss.

thanks very much russlar, bodhi.zazen,
i asked this because both the folders shows size of that particular partitions for eg c and C both showed 43Gb....


Also, the output of **gksudo gedit /etc/fstab** is

```
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda10 :
UUID=a412adb7-fa7e-4c8b-b345-143401093394 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda11 :
UUID=e1d738b9-a156-45ca-bb80-31f620d2c0b7 /home ext3 relatime 0 2
# Entry for /dev/sda9 :
UUID=1f1cd85a-ed8d-46d0-b78b-68955727ae2d none swap sw 0 0
/dev/scd1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd0 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sda8 /media/G ntfs defaults 0 0
/dev/sda7 /media/F ntfs defaults 0 0
/dev/sda6 /media/E ntfs defaults 0 0
/dev/sda5 /media/D ntfs defaults 0 0
/dev/sda1 /media/C ntfs defaults 0 0
```
(i hope i did this correctly!!)

Did 
[B]/dev/sda8 /media/G ntfs defaults 0 0
/dev/sda7 /media/F ntfs defaults 0 0
/dev/sda6 /media/E ntfs defaults 0 0
/dev/sda5 /media/D ntfs defaults 0 0
/dev/sda1 /media/C ntfs defaults 0 0[/B]
means that all the NTFS partitions are and will be automatically mounted for **read write**??
please help.... :(

---

### Post by karlr42 on 2008-09-18
> **Nabanna said:**
> thanks very much russlar, bodhi.zazen,
i asked this because both the folders shows size of that particular partitions for eg c and C both showed 43Gb....


Also, the output of **gksudo gedit /etc/fstab** is

```
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda10 :
UUID=a412adb7-fa7e-4c8b-b345-143401093394 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda11 :
UUID=e1d738b9-a156-45ca-bb80-31f620d2c0b7 /home ext3 relatime 0 2
# Entry for /dev/sda9 :
UUID=1f1cd85a-ed8d-46d0-b78b-68955727ae2d none swap sw 0 0
/dev/scd1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd0 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sda8 /media/G ntfs defaults 0 0
/dev/sda7 /media/F ntfs defaults 0 0
/dev/sda6 /media/E ntfs defaults 0 0
/dev/sda5 /media/D ntfs defaults 0 0
/dev/sda1 /media/C ntfs defaults 0 0
```
(i hope i did this correctly!!)

Did 
[B]/dev/sda8 /media/G ntfs defaults 0 0
/dev/sda7 /media/F ntfs defaults 0 0
/dev/sda6 /media/E ntfs defaults 0 0
/dev/sda5 /media/D ntfs defaults 0 0
/dev/sda1 /media/C ntfs defaults 0 0[/B]
means that all the NTFS partitions are and will be automatically mounted for **read write**??
please help.... :(
Yes, I think so. Just replace "defaults" with:
```
auto,user,exec,rw
``` instead. rw means read-write
They're not mounted right now, reboot or do the mount -a command someone mentioned and they should automatically mount.

---

### Post by bodhi.zazen on 2008-09-18
no, if you want to have read-write you need to use ntfs-3g (not ntfs).

From the fstab link :

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

> UUID=12102C02102CEB83  /media/windows  ntfs-3g  [noparse]auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=137[/noparse]   0  0Or in your case :

```
/dev/sda1 /media/C **ntfs-3g  [noparse]auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=137[/noparse] **0 0
```**_Note_**: [COLOR=darkred]There is no space in "fmask=137", for some reason the forums renders this information with a space[/COLOR].

If you want more lax permissions use :

dmask=000,fmask=111

You can list your partitions by UUID with :

```
sudo blkid
```

If you wish, you then replace "dev/sda" with "UUID=xxx-yyy-zzz"

---

### Post by Nabanna on 2008-09-24
Thanks a lot.

(the former method worked and now the windows partitions are automatically mounting and are having access for read write...
Do i still need **/dev/sda1 /media/C ntfs-3g  auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=137 0 0**)

---

### Post by tenzinmonlam on 2008-11-12
Hi!!

I think i found the easy and perfect solution for the disk auto mount issue. While going through the add and remove application on ubuntu. I just installed the Disk manager out of curiosity. Bang that worked. Should check that out as well. You just have to do minor settings change ( on advance configuration just check mark your other drives). That will do the trick. You will have all the NTFS /FAT drivers on the desktop and you don't have to change any thing on other user profile. 
Disk Manager Home Page:

[http://flomertens.free.fr/disk-manager/](http://flomertens.free.fr/disk-manager/)

I hope this will work for you as well.

Peace...

---

