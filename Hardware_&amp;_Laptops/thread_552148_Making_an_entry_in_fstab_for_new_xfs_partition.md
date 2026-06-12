---
title: "Making an entry in fstab for new xfs partition"
date: 2007-09-16
forum: Hardware &amp; Laptops
---

### Post by cinematography on 2007-09-16
I formatted my ext3 sda4 partition to use the xfs filesystem. I tried to update the fstab, but when I rebooted, I couldn't mount that partition without first entering a password. I tried changing the permissions on the /media/sda4 folder for read/write, read only, read only with the file manager, with the group set to my group, but that didn't work either.

Here is my fstab file:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=41778420-b400-4284-9cf5-dc39b70931db /	ext3	defaults,errors=remount-ro	0       1

# /dev/hdb1
/dev/hdb1		/media/hdb1	ext3	defaults,errors=remount-ro		0       1

# /dev/sda2
UUID=2C88743C8874071C	/media/sda2	ntfs	defaults,nls=utf8,umask=007,gid=46	0       1

[COLOR="Red"]# /dev/sda4
UUID=7d8cfa29-9670-4c19-9e93-fd5993462273	/media/sda4	xfs	defaults	0       1[/COLOR]

# /dev/sda1
UUID=224ee0d5-1338-49eb-a961-1aad6c32d75f	none		swap	sw		0       0

/dev/hda		/media/cdrom0   udf,iso9660 user,noauto				0       0
```

Any help with this problem would be greatly appreciated.

---

### Post by cinematography on 2007-09-17
A nice user on [LinuxQuestions.org]("http://www.linuxquestions.org") gave this solution and it fixed the problem: 

[QUOTE=jschiwal]If this is an external drive, then it should mount for you the next time you restart the system.  You can use sudo to mount it in the meantime.  If it is an external drive then you don't want it to mount automatically at boot time, in case either the device isn't plugged in, or it is assigned to another device such as /dev/sdc4.

In that case, add the "noauto" option.  If you want to mount it manually as a normal user, then add the "user" option.[/QUOTE]

---

