---
title: "cant write to second hard drive"
date: 2009-05-09
forum: Hardware
---

### Post by Hoobashank on 2009-05-09
i recently installed a second sata hard drive to my system. i went through and formatted it in ext3. I mounted the drive to /media/x.I also edited my /etc/fstab to mount it on startup.  

I am unable to write any files to the new drive. It tells me that i dont have permissions to write to the drive any time i try to do anything. I have tried the chown to change the owner, but it automatically switches back to root and i am still unable to write files. here is my fstab: 

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=999ef006-b87b-482f-9e13-f04f612e3f51 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=af15e561-3777-4b5d-bec3-3bac761ffdcf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1    /media/x   ext3    defaults     0        2

Any help is greatly appreciated. 
Thanks!

---

### Post by 73ckn797 on 2009-05-09
Have you restarted the computer since making the changes? I just installed a new drive and could not access it until a restart. It may be that simple.

---

### Post by fdrake on 2009-05-09
did u try changing the line like this..
```
/dev/sdb1 /media/x ext3 auto rw,user,noauto,exec 0 0
```

---

### Post by Hoobashank on 2009-05-10
if i try changing the line to the above, when i try to mount the drive it says

[mntent]: line 15 in /etc/fstab is bad

i have also tried restarting my computer, it didnt work. the owner changes back to root every time. i can copy files to folders within the drive, bit if i try to move something to the root of the drive it says permission denied. 
any help is greatly appreciated.
Thanks!

---

