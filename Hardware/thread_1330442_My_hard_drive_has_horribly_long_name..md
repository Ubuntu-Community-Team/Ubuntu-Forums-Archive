---
title: "My hard drive has horribly long name."
date: 2009-11-18
forum: Hardware
---

### Post by GaretJax on 2009-11-18
I installed Ubuntu 9.10 from CD last night and this is the path to my secondary hard drive "/media/9fcc9f71-c374-47f9-ab69-028c3a717d1e".  A name like this will make pathing very difficult.

How did it get a name like that and how can I change it?

---

### Post by SlugSlug on 2009-11-18
```
gksudo gedit /etc/fstab
```edit the path in there IE
/dev/sdb1 /media/[[bunch of numbers]]  change to
/dev/sdb1 /media/Stuff
& create the directory, IE 
```
sudo mkdir /media/Stuff
```

---

### Post by GaretJax on 2009-11-18
My drive name is not listed in that file.  Here is the file data:

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=cde45715-88c1-4442-b270-0a031d539997 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b95a2027-4c41-43fa-ba35-5444aa84b1c0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by SlugSlug on 2009-11-18
is that the whole fstab file?

---

### Post by GaretJax on 2009-11-18
Yes.

---

### Post by SlugSlug on 2009-11-18
could you show me the output of 
df 
and
ls /dev/sd*

---

### Post by sisco311 on 2009-11-18
> **GaretJax said:**
> I installed Ubuntu 9.10 from CD last night and this is the path to my secondary hard drive "/media/9fcc9f71-c374-47f9-ab69-028c3a717d1e".  A name like this will make pathing very difficult.

How did it get a name like that and how can I change it?

Go to System -> Administration -> Disk Utility, select the partition and change the label. Remount it; it should mount in /media/LABELNAME.

---

### Post by GaretJax on 2009-11-18
df output is
> Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             36843208   2672272  32299368   8% /
udev                    768004       252    767752   1% /dev
none                    768004       996    767008   1% /dev/shm
none                    768004        88    767916   1% /var/run
none                    768004         0    768004   0% /var/lock
none                    768004         0    768004   0% /lib/init/rw
/dev/sdb1            241269024   1236036 227777152   1% /media/9fcc9f71-c374-47f9-ab69-028c3a717d1e

And ls /dev/sd* is:
> /dev/sda  /dev/sda1  /dev/sda2  /dev/sda5  /dev/sdb  /dev/sdb1


---

### Post by GaretJax on 2009-11-18
I used the disk utility and that fixed my problem.

Thank you.

---

### Post by sisco311 on 2009-11-18
> **GaretJax said:**
> I used the disk utility and that fixed my problem.

Thank you.

You're welcome!

Please mark your thread as [SOLVED] by selecting **Mark this thread as solved** from the [color="Red"]Thread tools[/color].

---

