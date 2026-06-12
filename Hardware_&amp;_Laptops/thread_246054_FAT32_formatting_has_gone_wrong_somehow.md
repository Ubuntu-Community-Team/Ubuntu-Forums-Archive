---
title: "FAT32 formatting has gone wrong somehow"
date: 2006-08-28
forum: Hardware &amp; Laptops
---

### Post by autrui on 2006-08-28
hi all,

im still pretty new at linux, but i think i'm doing ok.  but yet again im stumped.  so i have a 250gig IDE hd that was, until a few minutes ago, formatted NTFS.  i backed up all my stuff to convert it to FAT32, because i'd rather have the sense of security--there's a lot of important stuff destined for that drive.  

so i formatted it through gparted, and couldn't mount it, so i did it again using System>Administration>Disks, and still can't mount it.  the relevant line in fstab now looks like this:
```

/dev/hda1    /media/windows vfat  nls=utf8,umask=0000 0    0

```

here's what i'm seeing when i try to mount it:

```
nic@blackbox:~$ sudo umount -a
umount: /dev: device is busy
umount: /var/run: device is busy
umount: /: device is busy
nic@blackbox:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
so then i try:
```

nic@blackbox:~$ dmesg | tail
[17179606.148000] Bluetooth: RFCOMM ver 1.7
[17179609.476000] eth0: no IPv6 routers present
[17179635.776000] Warning: /proc/ide/hd?/settings interface is obsolete, and will be removed soon!
[17179639.032000] FAT: Unrecognized mount option "nls=utf8" or missing value
[17180009.324000] FAT: Unrecognized mount option "nls=utf8" or missing value
[17180226.936000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17180226.936000] FAT: bogus number of reserved sectors
[17180226.936000] VFS: Can't find a valid FAT filesystem on dev hda1.
[17186499.812000] FAT: Unrecognized mount option "nls=utf8" or missing value
[17186517.412000] FAT: Unrecognized mount option "nls=utf8" or missing value
nic@blackbox:~$

```

does anyone know what the source of this problem is?  is it a bad formatting?  is it fstab?  i didnt somehow fry this drive, did i?

thanks!

autrui

---

### Post by autrui on 2006-08-30
anyone seen anything like this before?

thanks,

autrui

---

### Post by autrui on 2006-08-31
got an answer.  doing the stuff mentioned by fluffnik in the last post in this thread: 

[http://ubuntuforums.org/showthread.php?t=246584&highlight=mount+vfat](http://ubuntuforums.org/showthread.php?t=246584&highlight=mount+vfat)

made it work perfectly.

autrui

---

