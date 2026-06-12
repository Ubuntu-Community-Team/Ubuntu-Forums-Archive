---
title: "[SOLVED] automount ntfs hard disk"
date: 2007-12-18
forum: Hardware &amp; Laptops
---

### Post by xodroolis on 2007-12-18
i have a second hard drive that needs to be auto mount at the start up
its name is "secondary hard"
its filesystem is ntfs

the fstab files is as follows

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=314e3b90-6768-44a5-b144-0fd5224d590f /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=acf8e8d7-3a8b-4fae-aa48-28d7fecba6bf none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

tell me what more info you need to guide me what to change in fstab
thanks anyway
:-D

---

### Post by taurus on 2007-12-18
Is it /dev/hdb1?  
```
sudo fdisk -l
```

Which Ubuntu release are you running?

---

### Post by xodroolis on 2007-12-18
ubuntu 7.10

---

### Post by xodroolis on 2007-12-18
sudo fdisk -l    gives:


Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x11da11da

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4787    38451546   83  Linux
/dev/hda2            4788        4998     1694857+   5  Extended
/dev/hda5            4788        4998     1694826   82  Linux swap / Solaris

Disk /dev/hdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf9210cb8

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       30401   244196001   42  SFS

---

### Post by ajgreeny on 2007-12-18
There is no ntfs file system disk showing in the fdisk output so I assume it is not yet formatted as ntfs, but maybe something else.  Also I am not even certain that the disk is attached to the computer, unless it is the 250GB hdc, shown as

Disk /dev/hdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf9210cb8

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       30401   244196001   42  SFS

If that is so then you will need to make sure that you have ntfs-3g installed along with libntfs-3g12 and also probably ntfs-config.  You can then set up the mounting of the disk and read/write permissions.

---

### Post by xodroolis on 2007-12-18
yes exactly
the 250 gb disk is the one i want to be automounted
the libntfs-3g12 is installed
can you guide me further?

---

### Post by ajgreeny on 2007-12-18
Is it already formatted to ntfs?  If so, in your menu go to **System Tools->NTFS Configuration Tool** and you should find what you need.

---

### Post by xodroolis on 2007-12-18
let me be more specific
first of all i am new to ubuntu
this hard disk is already ntfs formated under windows
I have 2 disks 
the 1st 40gb was recently formated and got ubuntu installed on it
the 2nd has only files (no operating system, it never had)
I can see the 2nd disk , i can write and erase files
but as i ve been told it is not auto mounted and it only works when i manually access it
there is no System Tools->NTFS Configuration Tool as you say in my menus
thanks if you bother

---

### Post by ajgreeny on 2007-12-18
Make a new folder for mounting eg ```
sudo mkdir /media/hdc1
```Now edit your /etc/fstab file as root ```
gksudo gedit /etc/fstab
```which will allow you to open the file and edit it as root.

Add the following line to your fstab file:-
[B]/dev/hdc1       /media/hdc1  ntfs    nls=utf8,umask=0222 0       0
[/B]It should now mount at the next boot, but you can check it straight away with ```
sudo mount -a
``` in terminal.

It is possible you needed to edit your menus with a right click in the menu bar and then add the NTFS items I mentioned earlier to do it the other way, but I don't know for certain.

---

### Post by xodroolis on 2007-12-18
propably i have done something wrong from the begining
nothing happened as i followed your steps
sudo mount -a
gives me nothing at all
note that i only see the 2nd disk on the explorer
I am the administrator of the 1st disk but i cant be the administrator of the second (i remind you that the 2nd drive existed as it is now in a different system before based on windows, not over the 2nd but over the 1st) It names an administrator "root"
At the installation of ubuntu i didnt anything for the 2nd drive
but i can see it and write or delete files on it
But i cant see it on the disk space analyser for example

here is the fstab file after what you told me to do

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1

UUID=314e3b90-6768-44a5-b144-0fd5224d590f /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=acf8e8d7-3a8b-4fae-aa48-28d7fecba6bf none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/hdc1 /media/hdc1 ntfs nls=utf8,umask=0222 0 0

oh! and no NTFS Configuration Tool at all anywhere i looked

---

### Post by xodroolis on 2007-12-18
ok!
it works now!
thank you for your time!!!

---

### Post by brad1138 on 2007-12-31
> oh! and no NTFS Configuration Tool at all anywhere i looked

I know this is solved but just to tie up this loose end, I couldn't find it either. You have to add it from "Add/Remove" in applications. In Add/Remove I typed in "ntfs conf" in the search bar and that was enough to bring it up. Click the check box then "apply changes" and it's there. It worked also, just run it and select drive to mount and it automounts after reboot, very easy.

Brad

---

