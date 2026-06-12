---
title: "Unable to mount ipod"
date: 2007-12-15
forum: Hardware &amp; Laptops
---

### Post by stickmangumby on 2007-12-15
I'm having trouble mounting my iPod with Ubuntu 7.10. It used to work fine (under 7.04). It works fine with Windows XP on the same computer.

```
$ cat /proc/scsi/scsi 
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: Apple    Model: iPod             Rev: 1.62
  Type:   Direct-Access-RBC                ANSI  SCSI revision: 00
```

```
$ sudo mount
/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/hdc1 on /home type ext3 (rw)
/dev/hda1 on /media/hda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)

```

```
$ sudo mount /dev/sda /media/ipod/
mount: you must specify the filesystem type
$ sudo mount -t vfat /dev/sda /media/ipod/
mount: /dev/sda: can't read superblock
$ dmesg | tail
[  714.443009] end_request: I/O error, dev sda, sector 0
[  714.444045] end_request: I/O error, dev sda, sector 0
[  731.310179] end_request: I/O error, dev sda, sector 0
[  731.310192] FAT: unable to read boot sector
[  773.683679] end_request: I/O error, dev sda, sector 0
[  773.683696] FAT: unable to read boot sector
[  775.040073] end_request: I/O error, dev sda, sector 0
[  775.040086] FAT: unable to read boot sector
[  775.588016] end_request: I/O error, dev sda, sector 0
[  775.588129] FAT: unable to read boot sector
```

I can't figure it out! It simply won't automount, and nothing I do to mount it gets it working. Has anyone got any idea how to fix it? Thanks a lot :)

---

### Post by IcarusR on 2007-12-16
Hi,

Just got my iPod to work in 7.04 with Amarok. I followed this Howto....
> [http://ubuntuforums.org/showthread.php?t=619615](http://ubuntuforums.org/showthread.php?t=619615)
iPod now auto mounts, just like a CD & in Amarok can see mp3s on it once you have 'connected' it.

Hope this helps.

Icarus

---

### Post by John Azelvandre on 2007-12-16
I'm having similar problems with my 2005 black ipod video (30Gig).  I'm not sure the linked tutorial is really necessary for my situation, as it is an older model.

My problem is that: Music Player, Amarok and the system all correctly recognize the ipod on hotplugging, but I can't write to the ipod.  (It was previously used with a Mac ibook which I no longer have access to).

When attempting to connect to the ipod through Amarok, I get a message which says "cannot write lockfile ... device is read-only."

With musicplayer, it can read the ipod fine, but I cannot copy any files over.

A few details:

```
Host: scsi5 Channel: 00 Id: 00 Lun: 00
```

and 

```
/dev/sdb3 on /media/John Azelvandre’s iPod___ type hfsplus (rw,nosuid,nodev)
```

Is there a simple solution to this problem?

Thanks in advance.

---

### Post by stickmangumby on 2007-12-17
What user:group owns the folder you're mounting your iPod in in /media?

---

### Post by John Azelvandre on 2007-12-17
It appears that the owner and the group are both "root."  This looks like a problem.  How can I change it to my user?
 
ls -l gives:

```
drwxr-xr-x 1 root root 8 2007-05-30 08:04 Calendars
drwxr-xr-x 1 root root 4 2000-01-01 03:44 Contacts
drwxr-xr-x 1 root root 9 2005-12-12 17:36 iPod_Control
drwxr-xr-x 1 root root 3 2000-01-01 03:44 Notes
drwxrwxrwx 1   99   99 4 2007-05-30 08:04 Photos
drwxr-xr-x 1   99   99 5 2007-12-12 21:07 RUFUS
```

---

### Post by John Azelvandre on 2007-12-17
I tried to change the permissions, but was unable to do so:

```
zizonus@hedgewizard2:/media$ sudo chmod o+rwx John\ Azelvandre’s\ iPod__/
[sudo] password for zizonus:
chmod: changing permissions of `John Azelvandre’s iPod__/': Read-only file system
```

???

---

