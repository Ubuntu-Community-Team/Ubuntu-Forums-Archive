---
title: "Help setting up RAID array"
date: 2009-04-23
forum: Hardware
---

### Post by pavsid on 2009-04-23
Hi all,

Just bought 2 x 1TB drives to set up as a RAID 1 array to safely store data on. I have another drive which holds the OS so just want the two new drives to show up as a single drive so i can start copying data across.

I've enabled raid on the two drives in the BIOS, and used the mobo RAID utility to set them as Mirrored, however when i boot into Ubuntu i can't see any drives anywhere. Issuing sudo fdisk -l shows the disks but that neither have valid partition tables.

Have read that i may need a RAID driver or software or somthing? Is this in addition to enabling it in the BIOS?

Any help appreciated, thanks

---

### Post by linux_paul on 2009-04-23
I ran into the same problem. This is common with motherboard raid controllers, they usually won't be recognized by Linux by default. You can search for a suitable driver, good luck, or you can use software raid like I did. 

You can quickly setup the raid by installing mdadm and giving the command mdadm --create /dev/md0 --level=0 /dev/sdb1 /dev/sdc1

Here is a great howto:
[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

---

### Post by pavsid on 2009-04-23
Thanks man, just what i was looking for, do i have to undo changes i made in the bios/raid setup before using software raid?

---

### Post by linux_paul on 2009-04-23
I would. It's too bad there is not more support for raid controllers with linux.

---

### Post by pavsid on 2009-04-23
Ok thanks, i'll have a play around and post back my findings as i think the guide is more geared towards installing linux on a RAID setup rather than  using one as storage on a current install

---

### Post by pavsid on 2009-04-23
Ok, i'm really not having much luck here. 

I've managed to create an array as /dev/md0, create a filesystem in it with mkfs /dev/md0 and then mount it in /media/DATA. 

I've also added the line /dev/md0 /media/DATA ext3 defaults 0 0 in fstab but the drive will not mount again at reboot

Also, i need this drive to be accessible/writable from windows PCs - is ext3 ok to use or must it be formatted as NTFS? (both drives or just the filesystem of the array?)

Thanks

---

### Post by linux_paul on 2009-04-24
The howto has a section about /etc/mdadm/mdadm.conf that needs to be setup for the drive to be assembled automatically at boot.

I have not run Windows for a while but I do recall a driver that allows you to read/write to ext3 filesystems.

---

### Post by pavsid on 2009-04-24
Hi,

I started from scratch removing any array entries and setting up a new one using
```
sudo mdadm --create /dev/md0 --level=1 --name=DATA /dev/sdb1 /dev/sdc1
```

have tried adding the following lines to the /etc/mdadm/mdadm.conf file:
```
DEVICE /dev/sdb* /dev/sdc*
ARRAY /dev/md0 name=DATA level=1 num-devices=2 auto=yes
```

and have added the following to fstab:
```
/dev/md0 /media/DATA ext3 defaults 0 0
```

..but it still does not mount at startup - i have to issue 
```
sudo mdadm -assemble /dev/md0 /dev/sdb1 /dev/sdc1
```

in order to mount the array which then appears in /media/disk rather than /media/DATA as stipulated in fstab

Am i completely missing something? I've read somewhere that the drives need to be formatted with raid flag set - is that still the case?

Thanks for your help Paul

---

### Post by pavsid on 2009-04-24
Think i've sorted this now, the location in fstab is incorrect and the ARRAY line in mdadm.conf is too.

I'll post back a step-by-step when i get home and have tested it properly

---

### Post by linux_paul on 2009-04-24
Here is my mdadm.conf file:
```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
#MAILADDR root
MAILADDR paul

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=adb6a17c:52fb3b7e:799f5a3b:588da548

# This file was auto-generated on Sat, 18 Apr 2009 22:17:49 -0700
# by mkconf $Id$

```

And my /etc/fstab:
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# / was on /dev/sda5 during installation
UUID=3aed453a-9f38-4e48-8012-2399226d248e /               ext4    relatime,errors=remount-ro 0       1

# /boot was on /dev/sda1 during installation
UUID=3763ac9d-d157-484b-9d95-9bcd0a9a865d /boot           ext3    relatime        0       2

# /home was on /dev/sda8 during installation
UUID=f842ed10-2e69-4c28-99cf-20ec55009801 /home           ext4    relatime        0       2

# /var was on /dev/sda6 during installation
UUID=42dd4aed-cdd7-4735-9b04-bfb93d7baabe /var            ext4    relatime        0       2

# swap was on /dev/sda7 during installation
UUID=22849686-b975-4060-81fc-a58b72bda786 none            swap    sw              0       0

# /dev/md0 Mirrored RAID drives, 2  320GB hard drives.
/dev/md0	/data		xfs		defaults	0	2

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

Hope this is helpful.

---

### Post by pavsid on 2009-04-24
Hi, yes that helps thanks.

Just one last thing, when i mount /dev/md0 it mounts as /media/disk - if i put anything different in fstab then it won't mount.  How do i get it so that it mounts as, ofr instance, /media/DATA or just /data like you have it?
Also, do i have to make a filesystem on /dev/md0 it or is that not necessary? I tried it, then mounted it, but it didn't seem to make any difference

---

### Post by linux_paul on 2009-04-24
Edit /etc/fstab and ensure the directory exists (remember case sensitive.) I got a superblock error when trying to mount it without formating it first, can't say much more about it.

---

