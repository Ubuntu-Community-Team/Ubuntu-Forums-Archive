---
title: "NTFS dirty bit"
date: 2006-04-19
forum: Hardware &amp; Laptops
---

### Post by auroraborealis on 2006-04-19
This isn't really a pressing issue, but I'd like to know if I can reset the NTFS dirty bit without rebooting into Windows?
```
$ sudo mount /media/Windows
Volume is dirty.
Run chkdsk and try again, or use the --force option.
Mount failed.
``` Or where do I use the --force option? Mount doesn't like it.

---

### Post by taurus on 2006-04-19
Shouldn't the mount command look something like
```

sudo mount -t ntfs /dev/hda1 /media/Windows

```
assuming that /dev/hda1 is where your XP is?

---

### Post by auroraborealis on 2006-04-19
It has an entry in /etc/fstab.

---

### Post by taurus on 2006-04-19
[QUOTE=auroraborealis]It has an entry in /etc/fstab.[/QUOTE]
Then what is the content of your /etc/fstab?

---

### Post by auroraborealis on 2006-04-20
The relevant one being

/dev/sda2          /media/Windows      ntfs-fuse noauto,gid=1002,umask=0002 0 0

---

### Post by taurus on 2006-04-20
What happens if you remove "-fuse" from ntfs???

---

### Post by auroraborealis on 2006-04-21
It'll mount as read-only. Which, in some cases, is fine, but doesn't really solve the issue at hand. Thanks anyway.

---

### Post by taurus on 2006-04-21
Try this...
```

/dev/sda2  /media/Windows  ntfs  defaults,umask=0222  0  0

```

---

### Post by auroraborealis on 2006-04-23
It's all irrelevant now since I rebooted and chkdsk'ed, but ntfs won't mount as rw without fuse. ```
$ cat /etc/fstab|grep Windows
/dev/sda2           /media/Windows      ntfs    defaults,noauto,gid=1002,umask=0002 0 0
$ cat /etc/mtab|grep Windows
/dev/sda2 /media/Windows ntfs rw,gid=1002,umask=0002 0 0
$ touch /media/Windows/test
touch: cannot touch `/media/Windows/test': Read-only file system
```

---

### Post by RRS on 2006-04-24
> It's all irrelevant now since I rebooted and chkdsk'ed, but ntfs won't mount as rw without fuse.

Did chkdsk eliminate "dirty" message and allow mounting with fuse?

If so when after reboot did you chkdsk, and with what command?

I'm asking because I got the same results trying to mount with fuse. Tried to "chckdsk" couple different ways but "command not found", never thought to reboot though.

Also couldn't figure out how to force.

In my case xp has a corrupted boot.ini file and won't boot, I've been suspecting this as cause of "dirty". Possible you have similar problem? 

Still, makes me wonder why I can mount read only with no complaints though.

Don't mean to hijack your thread but hopefully if someone can solve your problem it'll help me too.

---

### Post by auroraborealis on 2006-04-24
The dirty bit is set if Windows doesn't get shut down properly. So just reboot and shutdown, and it SHOULD clear the bit.

---

