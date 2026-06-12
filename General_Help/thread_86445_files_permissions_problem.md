---
title: "files permissions problem"
date: 2005-11-05
forum: General Help
---

### Post by Jst on 2005-11-05
I have a problem and it really confuses me. I have a seperate partition for /home and a seperate disk for my music, photos, etc and on this two partitions I have a strange problem. If the owner/group doesn't have execute permissions on the files it's unable to open the file. This however isn't the problem on the / partition. So right now I have this two partitions mounted with noexec, but that's not the right solution. I'm unable to open text files :???: I'm using ext3.

---

### Post by nightfly on 2005-11-05
Execute rights are needed to open and browse directories as well as executing files.

The description of your problem is unclear. I will need clarification on your disk setup.

It would be best if you could post the contents of /etc/fstab here.

---

### Post by Jst on 2005-11-05
[QUOTE=nightfly]Execute rights are needed to open and browse directories as well as executing files.[/QUOTE]

Oh. Didn't know that I need execute rights to open directories. Somehow when I've been on Debian it didn't seem like that. I could set read/write permissions on a dir and I was able to open the dir without any problem. So how can I set read/write permissions on the files in a directory(and subdirectorys) and keep execute permissions on the directories. 


[QUOTE=nightfly]The description of your problem is unclear. I will need clarification on your disk setup.[/QUOTE]

Well as it seems the problem was I didn't have execute permissions on the directories. So I gues the problem was that I couldn't open the directories and it didn't have much to do with the permissions on the files as I have thought.


[QUOTE=nightfly]It would be best if you could post the contents of /etc/fstab here.[/QUOTE]

Here it is.
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb3       /home           ext3    noexec          0       2
/dev/hda1       /media/hda1     ext3    noexec          0       2
/dev/hdb1       /media/hdb1     ntfs    umask=0222      0       0
/dev/hdb4       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by felix_stegerman on 2005-11-05
[QUOTE=Jst]Oh. Didn't know that I need execute rights to open directories. Somehow when I've been on Debian it didn't seem like that. I could set read/write permissions on a dir and I was able to open the dir without any problem. So how can I set read/write permissions on the files in a directory (and subdirectorys) and keep execute permissions on the directories.[/QUOTE]

# find /path/to/dir -type d -exec chmod 750 {} \;
# find /path/to/dir -type f -exec chmod 640 {} \;

This will set the permissions of directories to drwxr-x--- (750)
and of files to -rw-r----- (640). Both recursively.

You may want to use other permissions.
# man chmod
will give you more info.


Felix

---

### Post by Jst on 2005-11-06
Wow. Thanks a lot :D

---

### Post by cvmostert on 2005-11-24
Hi,

find /path/to/dir -type f -exec chmod 775 {} \;

worked GREAT for me... well so far... thank you so!

---

