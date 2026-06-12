---
title: "[SOLVED] move /home from seperate hard drive to same hard drive as /"
date: 2008-09-08
forum: General Help
---

### Post by jamesmorad on 2008-09-08
Hey everyone,

need some help moving /home directory. currently it is on a separate hard drive than the / root directory but i want to put it on the same hard drive because i have a different use for the old hard drive. here is a copy of my fstab, if it helps. 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=dd36c32b-1ea3-4985-a796-3721386f193c /               ext2    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=66a13e15-e40c-4d8b-92f9-0f8afdd43d5d /home           ext2    defaults        0       2
#/dev/sdc1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by mb_webguy on 2008-09-08
You might be able to do all of this by booting into recovery mode, but it would probably be easier to boot from a LiveCD.  If you do go the LiveCD route, just make sure you edit the correct fstab file.

If you have space on sdb, you can make another partition, copy everything from sda1 to it, change the mount point for sda1, and then mount the new partition as /home.

If you don't have unused space on the drive and just want to put /home on the same partition as your installation, then unmount sda1 and mount it someplace else, create a /home directory, and copy all of your information over from sda1 to the new /home directory.

Either way, you're basically just copying the data from the current /home to the new /home, and editing fstab so Linux looks in the right place.

---

### Post by sisco311 on 2008-09-08
1) comment out the fstab entry and reboot:
```
gksu gedit /etc/fstab
```in xubuntu:
```
gksu mousepad /etc/fstab
```>  # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=dd36c32b-1ea3-4985-a796-3721386f193c /               ext2    defaults,errors=remount-ro 0       1
# /dev/sda1
**#**[I]UUID=66a13e15-e40c-4d8b-92f9-0f8afdd43d5d /home           ext2    defaults        0       2
[/I]#/dev/sdc1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0                                        2) at the log in screen press Ctrl+Alt+F1 and login in the terminal


3) mount your old /home partition

```
sudo mount UUID=66a13e15-e40c-4d8b-92f9-0f8afdd43d5d /mnt
```or
```
sudo mount /dev/sda1 /mnt
```4) copy your home folder(s) to the new location:
```
cp -r /mnt/* /home
```5) press Ctrl+Alt+F7 and log in.

---

### Post by justleen on 2008-09-08
you can unmount /home without problems..

- go into a terminal (ctrl-alt-f1), login 
- sudo umount /home (make sure your current working dir is not /home/
- mount the "home" drive to /mnt (for example)
- copy the data to /home/
- remove the /home entry in fstab
-reboot

---

### Post by jamesmorad on 2008-09-08
Thanks everyone for the quick reply and help! I'm following sisco311's guide and right now im just waiting for /mnt/* to copy to /home. I'm not sure how long its going to take but df showed that /dev/sda1 was ~ 1.8GB.

I'll follow up with an edit once everything works.

edit:

OK so i did everything and when I login I get the error message:

"User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users."

---

### Post by jamesmorad on 2008-09-08
OK i solved that problem by using the -p switch to maintain all the stuff that was needed. thanks again for the solution all!

---

### Post by sisco311 on 2008-09-08
sorry, my fault.
you don't need to cp the files as root(step 4)

to restore the permissions run the 
following commands from a terminal:
```
sudo chown -R $USERNAME: $HOME
chmod 0644 $HOME/.dmrc
```

---

### Post by sisco311 on 2008-09-08
> **jamesmorad said:**
> OK i solved that problem by using the -p switch to maintain all the stuff that was needed. thanks again for the solution all!
Cool!
If your thread is solved, please mark it solved by selecting 
**Mark this thread as solved** from the **Thead Tools**

---

### Post by jamesmorad on 2008-09-08
if using sudo cp -rp worked, should i jsut stick with that?

edit sorry, I didnt refresh quick enough!

---

