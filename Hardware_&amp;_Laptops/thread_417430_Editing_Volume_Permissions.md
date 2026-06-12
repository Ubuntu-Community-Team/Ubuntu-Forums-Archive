---
title: "Editing Volume Permissions"
date: 2007-04-21
forum: Hardware &amp; Laptops
---

### Post by blackhole82 on 2007-04-21
I'm trying to change the permissions for several volumes on my computer.  They are already automatically mounted via fstab, but they are ready only.  I tried looking at the documentation for changing permissions with umask=000, but I can't get it to work for my other linux partition on my other hard drive.  It works fine for the two ntfs partitions.  Whenever I add umask=000 for the ext3 partition it doesn't even show up as visible on the desktop anymore.  Here is my edited fstab file:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=d549dc59-86d7-4827-b777-0a790579f048 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb1
UUID=dbf4d67c-7f9b-4b51-b30f-ebd44e8181ce /media/hdb1     ext3    umask=000       0       2
# /dev/hdb2
UUID=809060F49060F1D8 /media/hdb2     ntfs    defaults,nls=utf8,umask=000,gid=46 0       1
# /dev/sda1
UUID=6401D2926C9A1D33 /media/sda1     ntfs    defaults,nls=utf8,umask=000,gid=46 0       1
# /dev/hdb3
UUID=e5564b20-ae5c-4430-b855-9e58bb0fb140 none            swap    sw              0       0
# /dev/sda3
UUID=17bbefdc-d6c2-49a9-bda1-634464973436 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

hdb1 is the linux partition I want to have read/write access for all users on.  Can anyone tell me what I'm doing wrong, or what I need to do for it to get to work?  Also, what is an easy way to change the displayed name of the volumes?  I guess I would need to unmount all the volumes, delete the folder for the mount point, and make a new folder, then mount them again.

---

### Post by super breadfish on 2007-04-22
Have you tried the instructions on this page?

[http://www.psychocats.net/ubuntu/mountlinux]("http://www.psychocats.net/ubuntu/mountlinux")

I had similar problems after installing and mounting a new ext3 formatted hard drive this morning. After using the commands to set the right permissions at the bottom of the page I could write to it.

I'm still a fairly new user, and I've found mounting issues confusing. Good luck :grin:

---

### Post by adromidon on 2007-05-01
I tried that guide and Ubuntu still acts like i have no access rights to the new HD I am going to try starting over and take it step by step again to see if i missed something

---

### Post by adromidon on 2007-05-01
Ok it works yeay for some reason the folder i made prior to following this guide did not want to change perms so I just made the storage one as the tutorial said and it works now :)

---

