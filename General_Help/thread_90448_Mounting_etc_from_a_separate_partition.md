---
title: "Mounting /etc from a separate partition"
date: 2005-11-15
forum: General Help
---

### Post by organgtool on 2005-11-15
I am attempting to perform the infamous trick of mounting /etc from another partition.  The reason I am doing this is because I want to mount the / partition as read-only for paranoid security, but I would like to be able to umount /etc to swap to a normal fstab file so that I can reboot into an "update" environment where I can upgrade all of the packages on my system.  I copied the fstab file on the /etc partition to /etc on the / partition to create a stub file for booting.  That fstab looks like this:


```
# <file system>  <mount point>   <type>       <options>      <dump>  <pass>
proc             /proc           proc         defaults       0       0
/dev/sda1        /               xfs          defaults       0       1
/dev/sda9        /etc            xfs          defaults       0       2
/dev/sda7        /home           xfs          defaults       0       2
/dev/sda5        /tmp            xfs          defaults       0       2
/dev/sda8        /var            xfs          defaults       0       2
/dev/sda6        none            swap         sw             0       0
/dev/hdc         /media/cdrom0   udf,iso9660  user,noauto    0       0
/dev/fd0         /media/floppy0  auto         rw,user,noauto 0       0
```


In theory, Ubuntu should mount the / partition during bootup, use the /etc/fstab stub file on that partition, and then attempt to mount the /etc partition over top the /etc directory on the / partition.  This method is supposed to work for many versions of Linux and BSD, but I am not having any luck accomplishing this in Ubuntu.  [edit]However, in practice, Ubuntu stops booting and asks which runlevel I would like to enter which shows that mounting the /etc partition over top of the existing /etc directory failes for some reason.[/edit]  Is there something I am missing or is there something unique about this situation in Ubuntu?  I appreciate any help you may provide.   Once I get the /etc partition to mount, I will add the "ro" parameter to the / partition as well as "noexec" to /var and /tmp.

---

### Post by nagilum on 2005-11-15
It's not as easy as adding the fstab file. After your kernel mounted the root partition it calles /sbin/init which relies on files that reside in /etc. These files also do the mounting of partitions from /etc/fstab, your new /etc cannot get mounted without the missing files.
Maybe you should make yourself more familiar with the boot process. Also, an initial ramdisk might be an easier way to accomplish what you are trying to do.

---

