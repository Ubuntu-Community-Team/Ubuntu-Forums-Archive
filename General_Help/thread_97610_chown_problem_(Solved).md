---
title: "chown problem (Solved)"
date: 2005-12-01
forum: General Help
---

### Post by WebDrake on 2005-12-01
Hello all,

I've set up my system with a FAT32 partition to enable both Linux and Windows access.  Let's call this partition /dev/hdaX.

The problem is that everything in the folder is listed as being owned by root, and I cannot change this with the chown command.  Let's suppose the drive is mounted as /media/hdaX and that I am inside the mount directory.  Then, I type,

sudo chown -R username.usergroup *

but am refused permission to reassign the ownership.

Any ideas why?  The aim here is that the mount directory /media/hdaX and the contents of this partition should be read/write/executable and owned by the group "usergroup".

Many thanks,

        -- Joe

---

### Post by tlc on 2005-12-01
Does FAT32 even support permissions? Can you copy the files elsewhere, chown them there, then copy them back?

---

### Post by suRoot on 2005-12-01
FAT32 doesn't support this, period.

---

### Post by WebDrake on 2005-12-01
[QUOTE=suRoot]FAT32 doesn't support this, period.[/QUOTE]

Okie.  Then why can't I write to the drive? :-(

---

### Post by frodon on 2005-12-01
Your fstab line should be the problem, post your fstab file and we will tell you the missing options : ```
sudo gedit /etc/fstab
```

---

### Post by WebDrake on 2005-12-01
[QUOTE=frodon]Your fstab line should be the problem, post your fstab file and we will tell you the missing options[/QUOTE]

Thanks v. much!  Here it is:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               reiserfs notail          0       1
/dev/hda7       /home           reiserfs defaults        0       2
/dev/hda1       /media/hda1     vfat    defaults        0       0
/dev/hda2       /media/hda2     ntfs    defaults        0       0
/dev/hda5       /liquorboy      vfat    defaults        0       0
/dev/sda1       /media/sda1     vfat    defaults        0       0
/dev/sda2       /media/sda2     ntfs    defaults        0       0
/dev/sda3       /media/sda3     vfat    defaults        0       0
/dev/sdb1       /media/sdb1     vfat    defaults        0       0
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

/dev/hda5 is the drive, but I've been having the same write problems with the /sda and /sdb drive (USB drives).

---

### Post by frodon on 2005-12-01
modify your file like that : ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               reiserfs notail          0       1
/dev/hda7       /home           reiserfs defaults        0       2
**/dev/hda1       /media/hda1     vfat    iocharset=utf8,rw,user,exec,umask=000        0       0**
**/dev/hda2       /media/hda2     ntfs    nls=utf8,user,auto,umask=0222        0       0**
[B]/dev/hda5       /liquorboy      vfat    iocharset=utf8,rw,user,exec,umask=000        0       0
/dev/sda1       /media/sda1     vfat    iocharset=utf8,rw,user,exec,umask=000        0       0[/B]
**/dev/sda2       /media/sda2     ntfs    nls=utf8,user,auto,umask=0222        0       0**
[B]/dev/sda3       /media/sda3     vfat    iocharset=utf8,rw,user,exec,umask=000        0       0
/dev/sdb1       /media/sdb1     vfat    iocharset=utf8,rw,user,exec,umask=000        0       0[/B]
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```Then do a "sudo mount -a" or reboot if it doen't work

Here are some details about the options : [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by WebDrake on 2005-12-01
Many thanks Frodon!  A reboot was necessary, but now all is working well. :-)

Best wishes,

       -- Joe

---

