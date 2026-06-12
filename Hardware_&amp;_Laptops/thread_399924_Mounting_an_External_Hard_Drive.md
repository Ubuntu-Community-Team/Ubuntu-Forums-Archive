---
title: "Mounting an External Hard Drive"
date: 2007-04-02
forum: Hardware &amp; Laptops
---

### Post by BrettRS on 2007-04-02
Hello,

Recent convert to Ubuntu here, have tried it before but didn't get into it because I didn't want to take the time to learn commands or use the terminal.  Anyway, to the problem.

(I have searched but didn't find any relevent information)

When I first installed Ubuntu, my external hard drive would mount and my two partitions would show up on the desktop.  Recently, not sure on the exact date, it wouldn't do this.  I have tried Automatix's Read/Write NTFS partition program but that didn't help.  It is a Maxtor One-Touch 80GB external hard drive.  This is the output of the fdisk -l command:

```
Disk /dev/hda: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1275    10241406   83  Linux
/dev/hda2            1276        1405     1044225   82  Linux swap / Solaris
/dev/hda3            1406        5005    28917000   83  Linux

```

I am currently using Ubuntu Edgy.

Thanks in advance,

Brett

---

### Post by davidgarcin on 2007-04-02
hey Brett,
I would try editing your /etc/fstab file (you'll need su rights to do this).  Add a line for your external hard drive that looks something like this:

```
/dev/sdb1  /media/files  vfat defaults,utf8,umask=007,gid=46 0 1
```

That's my entry for my WD 250 GB USB external drive.  "/dev/sdb1" is the system-assigned file system identifier.  For you, it will probably be /dev/hdb1.  The 'b' symbolizes the second hard disk, and the '1' symbolizes the first partition on that disk.

"/media/files" tells the system where in the root file system to mount your hard disk.

"vfat" is the file system type - FAT32 in this case.

the rest of the stuff is mounting options.  To tell you the truth, I can't remember what they all do, but Googling "fstab" should get you pretty far.  Those settings above give me automatic mounting and read/write access.

-Dave

---

### Post by BrettRS on 2007-04-03
Hello Dave,  

I've gotten my external to mount, but when I browse to it no files show up.  It shows up having 5.6 gigs of free space which is correct, but no files.  Any help?

Thanks,

Brett

---

### Post by stchman on 2007-04-03
> **BrettRS said:**
> Hello,

Recent convert to Ubuntu here, have tried it before but didn't get into it because I didn't want to take the time to learn commands or use the terminal.  Anyway, to the problem.

(I have searched but didn't find any relevent information)

When I first installed Ubuntu, my external hard drive would mount and my two partitions would show up on the desktop.  Recently, not sure on the exact date, it wouldn't do this.  I have tried Automatix's Read/Write NTFS partition program but that didn't help.  It is a Maxtor One-Touch 80GB external hard drive.  This is the output of the fdisk -l command:

```
Disk /dev/hda: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1275    10241406   83  Linux
/dev/hda2            1276        1405     1044225   82  Linux swap / Solaris
/dev/hda3            1406        5005    28917000   83  Linux

```

I am currently using Ubuntu Edgy.

Thanks in advance,

Brett

Ubuntu should mount the drives automatically.

---

### Post by davidgarcin on 2007-04-03
stchman:  yes, in theory Ubuntu should do it automatically, but I've had to do it manually before to get it to work.

Brett:  if you run the 'mount' command, what output does it give?

---

### Post by BrettRS on 2007-04-03
The output is as follows:

```
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-11-generic/volatile type tmpfs (rw)
/dev/hda3 on /home type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/hdd on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=brett)

```

---

### Post by stchman on 2007-04-03
> **davidgarcin said:**
> stchman:  yes, in theory Ubuntu should do it automatically, but I've had to do it manually before to get it to work.

Brett:  if you run the 'mount' command, what output does it give?

Is the external drive USB or firewire?

---

### Post by davidgarcin on 2007-04-03
Brett - From your mount output, it looks like it's not mounting at all - there's no mention of hdb in the list.  So I'm not sure what you mean when you say you've got it to mount.  Be more specific, and also post a copy of /etc/fstab.  Also, I'm assuming you rebooted since you modified fstab, but if you haven't, you should.
-Dave

---

### Post by BrettRS on 2007-04-03
Hello,

Well, I got it to mount and I'm an idiot for not catching it sooner.

It seems my USB cord was unplugged from the hard drive!

Anyway, thanks a lot guys, if I hadn't posted this I don't think I would've caught it!

Brett

---

