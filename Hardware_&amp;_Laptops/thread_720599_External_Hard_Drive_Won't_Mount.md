---
title: "External Hard Drive Won't Mount"
date: 2008-03-10
forum: Hardware &amp; Laptops
---

### Post by benf101 on 2008-03-10
[SIZE="4"]I know this has been SORT OF hashed out in other threads, such as: [/SIZE][http://ubuntuforums.org/showthread.php?t=710925](http://ubuntuforums.org/showthread.php?t=710925)
[SIZE="4"]
But I need it spelled out for me.  

When I try to mount my external Seagate 250 gig hard drive, I get the following message:[/SIZE]

[IMG]http://superthis.info/Files/mount_error.png[/IMG]

[SIZE="4"]If I just double-click it, it shows this:[/SIZE]

[IMG]http://superthis.info/Files/mount_error_first.png[/IMG]

[SIZE="4"]There is media in the drive, Windows sees it and everything runs fine on Windows.  Ubuntu is getting confused.  Where do I go from here?[/SIZE]

---

### Post by taurus on 2008-03-10
Can you at least mount it from a terminal?  Is it /dev/sdb1?  You can try something like

```
sudo mkdir /media/sdb1
sudo mount -t ntfs /dev/sdb1 /media/sdb1
df -h
```

---

### Post by benf101 on 2008-03-10
[SIZE="4"]Thanks, but it didn't work.  I got error message:[/SIZE]

[SIZE="3"]Failed to access '/dev/sdb1': No such file or directory[/SIZE]

[SIZE="4"]And it's not ntfs, I don't believe.  I think it's FAT32 or FAT.[/SIZE]

---

### Post by benf101 on 2008-03-24
Ok, mounting worked, but it is still not recognized any further than telling me it's mounted.  It still cannot see any data on the drive.  The error messages are  identical still. 

I did:
 sudo mkdir /media/sdd5
 sudo mount -t vfat /dev/sdd1 /media/sdd5
df -h


and got:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              46G   20G   25G  44% /
varrun                502M   92K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
udev                  502M  132K  502M   1% /dev
devshm                502M     0  502M   0% /dev/shm
/dev/sdb1             2.0G  1.7G  291M  86% /media/THUMB
/dev/sdd1             233G  162G   72G  70% /media/sdb5
/dev/sdd1             233G  162G   72G  70% /media/sdd5


But it still doesn't recognize that the drive has any data on it.

---

