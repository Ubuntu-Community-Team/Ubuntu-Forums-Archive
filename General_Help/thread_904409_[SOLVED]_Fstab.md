---
title: "[SOLVED] Fstab"
date: 2008-08-29
forum: General Help
---

### Post by CrusaderAD on 2008-08-29
I have added a network drive in my fstab file and rebooted. It now shows the drive in nautilus and on my desktop, but I get an error when trying to view it. Here's the error:

ls: cannot open directory .: Input/output error

Here's my fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9547a7c4-088c-4b8f-a114-b7532f5ddf3a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=fd2ed0aa-bc35-4162-896c-efe9f15508c1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
//192.0.1.1/folder/  /home/user/machine1/  cifs guest,uid=1000,iocharset=utf8,codepage=unicode,unicode 1 0  0
//192.0.1.1/folder/  /home/user/machine1/  cifs  username=admin,password=password1  0  0

---

### Post by momalle1 on 2008-08-29
Check this [http://ubuntuforums.org/showthread.php?t=288534]("http://ubuntuforums.org/showthread.php?t=288534")

---

### Post by CrusaderAD on 2008-08-29
When I do:

sudo mount -a

I get this:

mount error: mount point /home/user/machine1/ does not exist

---

### Post by Oldsoldier2003 on 2008-08-29
> **raptormanad said:**
> When I do:

sudo mount -a

I get this:

mount error: mount point /home/user/machine1/ does not exist

This means that the directory /home/user/machine1/ needs to be created so you can mount the volume there.

---

### Post by CrusaderAD on 2008-08-29
The directory is made, and it won't let me create another.

---

### Post by CrusaderAD on 2008-08-29
I took this out of my fstab file:

//192.0.1.1/folder/ /home/user/machine1/ cifs guest,uid=1000,iocharset=utf8,codepage=unicode,uni code 1 0 0

and rebooted. Now it works.

---

### Post by CrusaderAD on 2008-09-03
When I go to mount the same thing on another machine, I get this output in terminal:

[mntent]: line 10 in /etc/fstab is bad

Here's the line in my fstab:

//192.168.5.4/folder2/  /home/user/folder1/  cifs  username=admin,password=password1  0  0

---

### Post by CrusaderAD on 2008-09-03
It was the spaces... No spaces will make it work.

---

