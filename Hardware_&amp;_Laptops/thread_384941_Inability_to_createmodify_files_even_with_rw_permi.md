---
title: "Inability to create/modify files even with rw permissions"
date: 2007-03-15
forum: Hardware &amp; Laptops
---

### Post by Amackera on 2007-03-15
Hey everyone, I've been having a minor problem over the past little while that I can't figure out.

My situation is that I have an NTFS formatted external hard disk which has a ton (upwards of 100 GB) of stuff on it. I formatted it as NTFS before I switched to Linux and now that I realize that was a mistake, it's too late to fix it (there's no where to store my media temporarily without buying a new HDD).

My problem is that I've been having a LOT of trouble getting it to mount properly with the correct permissions. I have the ntfs-3g package installed from Synaptic, and I've added the following line to my fstab file:

```
/dev/sdc1 /media/exdisk1 ntfs-3g defaults,locale=en_US.utf8,umask=000 0 0 
```

When I try to create a directory (or delete one, or anything that modifies anything) I get an error about a deficient kernel FUSE module (see the attached screenshot).

In case anybody is at risk of thinking I'm a **complete** idiot, I DID follow the instructions in /usr/share/doc/ntfs-3g/README.Debian but still no luck :*(. Same error message.

Thanks in advance (hopefully)

-Anson

---

### Post by matburton on 2007-03-15
I would check out this guide
[http://www.ubuntuforums.org/showthread.php?t=217009]("http://www.ubuntuforums.org/showthread.php?t=217009")

Some very useful soul has created a repository that contains a modified version of fuse and pmount. Theres also a very small GUI which gives you a couple of ntfs mount options.

I would follow this guide (carefullly) and see if that works.

BTW you shouldn't need your altered fstab with this.

Hope that helps!

---

### Post by Amackera on 2007-03-20
Okay, I've done the things suggested in the guide, still no worky :(. 
I've gone as far as reinstalling ntfs-3g and fuse, still no luck, but now the problem has changed it's nature. Now I do not have permissions to read the disk unless I log in as root. 

Also, when logged in as root I still can't write/modify files in the drive, only read them (which defeats the purpose of using ntfs-3g). 

Also when I attempt to mount from the fstab, I get this error message in the console.

```
fusermount: mount failed: Device or resource busy
FUSE mount point creation error: No such file or directory
Unmounting /dev/sda1 ()

```

My fstab file reads like this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=c273f297-d13b-4075-9d4c-9890fb9af9df /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=983c3709-786c-4fb3-afe9-4b7b21e9eb35 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   	udf,iso9660 user,noauto     0       0
/dev/sdc1 	/media/exdisk1 	ntfs-3g defaults,locale=en_US.utf8    0    0 
/dev/sda1    	/media/windows  ntfs-3g defaults,locale=en_US.utf8    0    0

```

I'm thinking of just formatting my disk as FAT32 to avoid all these frickin' problems with NTFS support in Linux, but that still doesn't get me my Window's drive to mount (which must regrettably remain NTFS)

I appreciate all the help.

---

