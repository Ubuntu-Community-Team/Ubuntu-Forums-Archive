---
title: "Mount at boot -- editing fstab"
date: 2008-06-03
forum: Hardware
---

### Post by nicholas.Platt on 2008-06-03
I'm very much a newbie to the Linux scene, but I think I'm doing this right.
Thought that I would make sure before I restarted, however.

Is the the proper way to have my Windows partition mount at startup into Ubuntu?

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# Added by Nicholas
# /dev/sda1
UUID=505CF64D5CF62D7A    /media/disk/         ntfs

# /dev/sda6
UUID=56596d75-f36e-4776-acc3-9f4b90313345 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=0ac56f62-db1c-4de8-82cc-1a7a95cad694 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

References: [http://ubuntuforums.org/showthread.php?t=815029]("http://ubuntuforums.org/showthread.php?t=815029"), [http://www.linuxquestions.org/questions/linux-newbie-8/how-do-i-auto-mount-a-drive-at-boot-73103/]("http://www.linuxquestions.org/questions/linux-newbie-8/how-do-i-auto-mount-a-drive-at-boot-73103/")

---

### Post by llama320 on 2008-06-03
```
UUID# /media/windows ntfs nls=utf8,umask=0222 0 0
```

should work. If not, try

```
UUID# /media/windows ntfs defaults 0 0
```

just play around till you get it

Good Luck

EDIT: make sure /media/windows or /media/disk or /media/whatever exists before trying to mount it there. use

```
mkdir /media/whatever
```

to create the directory

---

