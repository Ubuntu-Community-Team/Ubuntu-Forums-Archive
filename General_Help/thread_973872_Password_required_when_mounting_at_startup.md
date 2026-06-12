---
title: "Password required when mounting at startup"
date: 2008-11-07
forum: General Help
---

### Post by fmeneuhe on 2008-11-07
Hi,
I have Kubuntu 8.10.
I have 2 internal hard drives with several NTFS  partitions in each one. 
When I first installed  kubuntu, the partitions were authomatically mounted at startup without any problems at all.
But now, at startup, one the ntfs partitios ask me for the root password, and it not used to be like this. Why now am I prompted for the root password? How can I solve this?
I want that my ntfs partition be auto mounted at startup without password as it used to be at first.
Thanks

---

### Post by roelpeeters on 2008-11-07
This is part of the new security policy. You can change this in the configuration file /etc/fstab; adding the options **auto, user** for each NTFS partition.

The option auto causes the drive to be automounted during startup. The option user means it will be mounted with the actual user.

Before touching this file, make a copy of your **fstab** file! To backup this file, start a terminal and type:
```

sudo cp /etc/fstab /etc/fstab.backup

```

Then edit the fstab file with your favourite text editor (I use gedit, you can also use vi, emacs, etc).

Roel

PS: this is not for the faint-hearted, so if you don't feel comfortable with the command line don't do it!

---

### Post by fmeneuhe on 2008-11-07
The  /etc/fstab has not any NTFS empty !! Here is a copy:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb6
UUID=2067ea41-5e08-4587-b888-398988a5b41e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=17090229-f01b-4113-b73c-064a6f1ea452 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


I do not understand anything. the system did not used to prompt me for a password when mounting ntfs partitions 2 or 3 days ago.

Thanks for any help.

---

### Post by fmeneuhe on 2008-11-08
Please, anyone has any idea how to sort it out?
Its driving me mad.
Thanks

---

