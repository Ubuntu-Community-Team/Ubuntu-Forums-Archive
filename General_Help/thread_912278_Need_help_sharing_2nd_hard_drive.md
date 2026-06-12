---
title: "Need help sharing 2nd hard drive"
date: 2008-09-06
forum: General Help
---

### Post by graphicwave on 2008-09-06
Hi All!
I am VERY new to Ubuntu so please go easy.  I have a box with a 350GB hard drive running Ubuntu 8.04.  The box is basically a file server for me to store files and access them with my Mac running 10.5.4.  A few months ago I followed a tutorial on how to setup my Ubuntu machine to share files with my Mac.  Everything went great...here is the tutorial [http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/)
I'm not using Time Machine.  Anyway, I just added a second hard drive to my Ubuntu machine and using the InstallingANewHardDrive tutorial ( [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive) ) I can only get so far.
I am using the ext3 partition for my new drive.  
I'm trying to create a mount point for my new drive every time it boots up, but when I get here    gksudo gedit /etc/fstab    I get an editing window that pops up, but there is nothing in it.  When I add the line I need to add and save, it says directory does not exist.  

Isn't there a simple way to just share the drive so my Mac can access it?  Do I have to go through all of that stuff?  I'm trying to create a mount point in my /home/username/ directory and everything works out, I just can't get it to do it automatically every time it boots up.  

All I want to do is share my 2nd hard drive...if there is an easy way to do this, please fill me in.  

Any help would be appreciated and, again, I'm new, so if anyone needs me to copy and paste any information, I can do that.  I think I'm just getting stuck at the fstab part.   Thanks in advance!

---

### Post by graphicwave on 2008-09-06
bump

---

### Post by graphicwave on 2008-09-06
bump  anyone know?

---

### Post by graphicwave on 2008-09-06
bump

---

### Post by tommynz1975 on 2008-09-06
> **graphicwave said:**
> bump

does anythng come up in terminal when you type

```
cat /etc/fstab
```

---

### Post by graphicwave on 2008-09-08
I get the following:
$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=18ba750c-3bfd-4787-ad0d-a846cded18b3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=3085ddc6-f146-4d1a-a13f-0a5ea1fad294 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

I have no idea what any of it means...

---

### Post by graphicwave on 2008-09-08
bump

---

### Post by DancingMan on 2008-09-08
> **graphicwave said:**
> I have no idea what any of it means...

Let's break it down.

Taking the second entry in your fstab:
> [COLOR="Red"]# /dev/sda1
UUID=18ba750c-3bfd-4787-ad0d-a846cded18b3[/COLOR] /               ext3    relatime,errors=remount-ro 0       1

The first part is the identifier of the partition.  It can be identifed by location (/dev/sda1) or by Universally Unique Identifier (UUID).  In this case, it is by UUID (the location /dev/sda1 has been commented out)

> # /dev/sda1
UUID=18ba750c-3bfd-4787-ad0d-a846cded18b3 [COLOR="Red"]/[/COLOR]               ext3    relatime,errors=remount-ro 0       1

The next part is the mount point.  This one is your root ("/").

> # /dev/sda1
UUID=18ba750c-3bfd-4787-ad0d-a846cded18b3 /               [COLOR="Red"]ext3[/COLOR]    relatime,errors=remount-ro 0       1

The third part is the filesystem type.  In this case, ext3.

> # /dev/sda1
UUID=18ba750c-3bfd-4787-ad0d-a846cded18b3 /               ext3    [COLOR="Red"]relatime,errors=remount-ro[/COLOR] 0       1

The 4th part is your mount options. The options specified in this case are:
relatime - only updates file access times if the previous access time is older than the modification time (As a result, improves system performance by reducing disk access).
errors=remount-ro - remounts the partition as read-only, if errors occur.

> # /dev/sda1
UUID=18ba750c-3bfd-4787-ad0d-a846cded18b3 /               ext3   relatime,errors=remount-ro [COLOR="Red"]0[/COLOR]       1


Fifth option is used by dump (backup utility).

> # /dev/sda1
UUID=18ba750c-3bfd-4787-ad0d-a846cded18b3 /               ext3   relatime,errors=remount-ro 0     [COLOR="Red"]1[/COLOR]


6th option is to tell fsck what order to check the filesystems in.  If zero, fsck won't check that filesystem.

---

### Post by DancingMan on 2008-09-08
> **graphicwave said:**
> when I get here    gksudo gedit /etc/fstab    I get an editing window that pops up, but there is nothing in it.  When I add the line I need to add and save, it says directory does not exist.

What if you try running
```
gksudo gedit
```
and then just opening /etc/fstab through gedit's File/Open menu?

---

### Post by graphicwave on 2008-09-09
Thanks for the descriptive information.  I am learning slowly but surely!

---

### Post by graphicwave on 2008-09-09
Once I found the file, it worked...I was able to complete the tutorial.  Thanks a lot!

---

