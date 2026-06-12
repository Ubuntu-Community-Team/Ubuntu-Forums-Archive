---
title: "ntfs partitions suddenly only mountable by root and read-only"
date: 2010-02-13
forum: Hardware
---

### Post by Thorondir on 2010-02-13
hi, everybody.

a friend of mine asked me to format one of his hard drives. he had windows on it, and he said, some problems with viruses.
i told him i could fix it. linux being safe from virus attacks.

so what i did is:
i plugged everything in and started my computer.
once in linux, i tried mounting the third [of three] partitions, to see what data i could save before formatting the whole thing. he said the only data he wanted was on it.

i ran avast! antivirus and it found a trojan, but could not delete it, it said that the filesystem was read-only.

i restarted the machine and booted windows, because windows lets you delete crucial data :P

it was a bad idea, because my antivirus [eset smart security 4] did nothing while the trojan multiplied onto all my other partitions.


now neither windows nor linux will let me modify those files. and my partitions in linux are all only mountable by the root user and that only in read-only mode.

any suggestions?

thanks

---

### Post by Thorondir on 2010-02-16
ok.
i was able to delete the trojan on all affected disks.

i did a chkdsk for all the drives in windows and they came back clean. but i still cant do anything with them but read off of them.

any ideas?

---

### Post by l1nuxfreak on 2010-02-16
Have you tried this?
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

If yes, copy all data on a new drive. Reformat :D

TIP:
On windows, always separate partitions of C: for /Windows and D: for /My Documents

On Linux, always separate partitions for / and /HOME

This way you can reformat C: and / and keep all your files intact.

---

### Post by amsterdamharu on 2010-02-16
What is the output of the following command?

```
more /etc/fstab
```

How did you mount them? Did you just click in nautilus because that should mount it in read write (unless there is something in fstab or windows did not unmount the drive correctly and you have to use -force option)

---

### Post by Thorondir on 2010-02-16
this is what i get

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults
                                                           0  0  
# / was on /dev/sda7 during installation
UUID=67b006af-a429-4020-9543-9349ccd2dd2a  /               ext4         errors=r
emount-ro                                                  0  1  
/dev/sda6                                  none            swap         sw      
                                                           0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noa
uto,exec,utf8                                              0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,
noauto,exec,utf8                                           0  0  
/dev/sdc1                                  /media/sdc1     ntfs         nls=iso8
859-1,ro,umask=000,gid=thorondir,user,owner,uid=thorondir  0  0  
/dev/sdd6                                  /media/sdd6     ntfs         nls=iso8
859-1,ro,umask=000                                         0  0  
/dev/sdd5                                  /media/sdd5     ntfs         nls=iso8
859-1,ro,noauto,umask=000                                  0  0  
/dev/sdd1                                  /media/sdd1     ntfs         nls=iso8859-1,ro,noauto,umask=000                                  0  0  
/dev/sdb1                                  /media/sdb1     ntfs         nls=iso8859-1,ro,noauto,umask=000                                  0  0  
/dev/sdb5                                  /media/sdb5     ntfs         nls=iso8859-1,ro,noauto,umask=000,user                             0  0  
/dev/sda1                                  /media/sda1     vfat         noauto                                                             0  0  
/dev/sdc6                                  /media/sdc6     ntfs         defaults                                                           0  0  
/dev/sda5                                  /media/sda5     ext2         defaults                                                           0  0  
/dev/sdc5                                  /media/sdc5     ntfs         defaults                                                           0  0  
/dev/sdf2                                  /media/sdf2     vfat         uid=root,group=thorondir,noauto,user                               0  0



sdc1 and sdd6 always automount.
in pysdm i hit configure.

haven't tried ntfs-3g yet.
i'll try and post the results.

---

### Post by Thorondir on 2010-02-16
so... 
gksu ntfs-config

gave me this:

Mounting /media/sdc6 failed.

ntfs-3g: Failed to access volume '/dev/sdc6': No such file or directory

ntfs-3g 2009.4.4 external FUSE 27 - Third Generation NTFS Driver

Copyright (C) 2005-2007 Yura Pakhuchiy
Copyright (C) 2006-2009 Szabolcs Szakacsits
Copyright (C) 2007-2009 Jean-Pierre Andre
Copyright (C) 2009 Erik Larsson

Usage:    ntfs-3g [-o option[,...]] <device|image_file> <mount_point>

Options:  ro (read-only mount), remove_hiberfile, uid=, gid=,
          umask=, fmask=, dmask=, streams_interface=, syncio.
          Please see the details in the manual (type: man ntfs-3g).

Example: ntfs-3g /dev/sda1 /mnt/windows


and


Mounting /media/sdc5 failed.

ntfs-3g: Failed to access volume '/dev/sdc5': No such file or directory

ntfs-3g 2009.4.4 external FUSE 27 - Third Generation NTFS Driver

Copyright (C) 2005-2007 Yura Pakhuchiy
Copyright (C) 2006-2009 Szabolcs Szakacsits
Copyright (C) 2007-2009 Jean-Pierre Andre
Copyright (C) 2009 Erik Larsson

Usage:    ntfs-3g [-o option[,...]] <device|image_file> <mount_point>

Options:  ro (read-only mount), remove_hiberfile, uid=, gid=,
          umask=, fmask=, dmask=, streams_interface=, syncio.
          Please see the details in the manual (type: man ntfs-3g).

Example: ntfs-3g /dev/sda1 /mnt/windows

Ntfs-3g news, support and information:  [http://ntfs-3g.org](http://ntfs-3g.org)

Ntfs-3g news, support and information:  [http://ntfs-3g.org](http://ntfs-3g.org)

so...
what now?

---

### Post by Thorondir on 2010-02-16
apparently the ntfs-3g fixed it. i don't know exactly how, but it did.

thanks guys :D

---

### Post by Thorondir on 2010-02-16
and just FYI...

the partitions sdc5 and sdc6 don't exist...

i don't know why it supposedly found them...

thanks

---

### Post by amsterdamharu on 2010-02-16
You could have removed the lines in fstab that had ntfs in it. Don't know what tool you used that put those lines in there but I would stay away from that tool as it says to mount everything **read only**.

For example:
/dev/sdd1 /media/sdd1 ntfs nls=iso8859-1,**ro**,noauto,umask=000 0 0

I let you guess what **ro** stands for. Not having that line in your fstab would enable nautilus to mount it when you click on it (the partitions should show up under computer).

Only when the ntfs has been badly unmounted you might have to mount it manually using sudo and the force switch.

---

### Post by Morbius1 on 2010-02-16
Agree 107.65% with amsterdamharu. This might be the classic example of why folks should never use pysdm. Not only is the ro an odd option but it's contradiced by the umask=000.

It seems that ntfs-config solved you're problem but I Personally would stay away from that one as well. I remember When I first installed it so I could find out what everyone was talking about. The first question it asked me when I launched it was: do I want to enable write ?. Was it not aware that write is enabled by default?

---

### Post by Thorondir on 2010-02-16
ok

thanks for the help and good advice.

it's great knowing that there's always someone that can help or give advice :D

another reason why i love the community that much.

---

