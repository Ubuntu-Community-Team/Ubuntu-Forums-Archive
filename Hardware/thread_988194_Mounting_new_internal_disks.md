---
title: "Mounting new internal disks"
date: 2008-11-20
forum: Hardware
---

### Post by msboston01 on 2008-11-20
Hello,

I just migrated from NAS-Lite 2.0 from server elements to Ubuntu to add some security features to my 6 disks NAS server.

I am having the hardest time setting up two drives that I had to format whithin Ubuntu using the partition editor (gparted). Gparted seems to be doing the work correctly, yet I couldn't write to these two disks. After trying multiple times a change of ownership (their properties were showing nouseid, nodev and rw) yesterday (sudo chown -R nicolas /media/) I manage to get them rw.

I shut the server down this morning to move it to its final and headless location and rebooted. At this point, the server (actually Ubuntu 8.10 desktop) won't mount the 2 drives and gives me a "Cannot Mount Drive" with a reason "You don't have the necessary privileges to mount these drives". I tried the magic chown again and no results.

Note: I am now VNCing in this headless machine. could this be a problem?

I had it... I spent 5 hours on these :mad: disks and now, I get this. Pleaaaaaaaaaaaase I need help.

Thanks

Nic

---

### Post by taurus on 2008-11-20
Post the outputs of these commands.

```
sudo fdisk -l
cat /etc/fstab
ls -la /media
```
I assume you try to mount those two drives from /etc/fstab?

---

### Post by msboston01 on 2008-11-20
Not sure about you assumption. I tried to mount them through the menu "Places" then select the drive name.

I also tried the mount command using sudo. 

```
nicolas@Mediacave:~$ sudo mount /dev/sde1
[sudo] password for nicolas:
mount: mount point /media/sde1 does not exist
```

Here is what is in the etc/fstab

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b3f059de-3617-454c-b325-abf4c755ef41 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=a3e79090-8f89-4acb-9ddc-f518d525fe0f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

I did a reboot just now and I managed to mount the disks. So I guess I don't have a problem anymore. :confused:

I have a feeling that my IDE controller card is resonsible and that Ubuntu not happy with it.

---

### Post by taurus on 2008-11-20
You can have your drives mount automatically each time you boot Ubuntu without clicking anything to mount them first unless that is what you want, clicking the drives to mount them.  All you need is to add two entries, one for each drive, in /etc/fstab.

---

### Post by msboston01 on 2008-11-20
Oh well that would be very sweet. What should I enter for say "/dev/sde1"? I'd like to have that done for all 6 drives too.

Thanks

Nic

---

### Post by taurus on 2008-11-20
What filesystem is /dev/sde1?  Just post the outputs of these commands and specify which six partitions/drives that you want to mount.

```
sudo fdisk -l
sudo blkid
```

---

### Post by msboston01 on 2009-11-06
Marking this thread solved with the help of Ubuntu 9.10 and LVM using KVPM.

---

