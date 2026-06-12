---
title: "Can't mount external USB 1 TB harddrive"
date: 2012-07-13
forum: Hardware
---

### Post by PDA1 on 2012-07-13
I've got a Buffalo external USB connected 1 TB hard drive that won't mount.

The drive appears in Disk Utilities under Disk Drives as being Device /dev/sdb 

The problem is it won't mount.

When issuing the following command here's what I get;

$ sudo mount /dev/sdb
[sudo] password for NONE: 
mount: can't find /dev/sdb in /etc/fstab or /etc/mtab

Gparted DOES NOT recognize of identify the drive.


As to another question. related to this one....is there a quick and fast way to format the drive?


Any ideas how to fix this?

Thanks

---

### Post by Cheesehead on 2012-07-13
> **PDA1 said:**
> $ sudo mount /dev/sdb

Take a look at [FONT="Courier New"]man mount[/FONT]. 
```
mount [-fnrsvw] [-t vfstype] [-o options] device dir
```
The way you're doing the mount command is fine...if the disk is already listed in /etc/fstab. That file fills in the rest of the info that mount needs. Specifically vfstype and dir.

Try something more like this once it's been partitioned and/or formatted.
```
sudo mount /dev/sdb -t your-format /media/your-mount-point
```
Though that's usually not neccessary. GVFS will normally mount the drive for you. Check dmesg and syslog for mounting errors (most likely format-not-recognized)


GParted can format the drive for you.

---

### Post by PDA1 on 2012-07-13
Thanks for suggestions but I have absolutely no idea how to fill in any of the options for what you mentioned.

Here's the odd thing-  The problem hard drive LED will blink like it's being accessed when I start Gparted but no reference to the drive (sdb) appears anywhere.

In Disk Utility it won't mount but is referenced therein.

Should I reformat the drive?  (there's NO data on it)

Any idea how long the reformat should take?  I'm running an old Dell Inspirion (2006 era) notebook.

thanks

---

### Post by Cheesehead on 2012-07-13
Are you saying that the Gparted application doesn't open properly?
Has Gparted worked for you in the past?
What happens when you start Gparted from the GUI?
What happens (including error messages) when you start Gparted from a terminal prompt?

Plug in the drive, then open a terminal window and try the following commands, and paste the repsonses here.
```
demsg | tail -n 20
cat /var/log/syslog | tail -n 10
```

---

### Post by typhoon_tip on 2012-07-13
Are you sure you are using a 3 way USB cable ? Do you have external power inlet for your hard drive ? I am pretty sure 1 TB drive require extra power, thus if you are using it with a single USB cable (end to end) it will never work.

---

