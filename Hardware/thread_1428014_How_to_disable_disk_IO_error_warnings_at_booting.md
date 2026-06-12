---
title: "How to disable disk I/O error warnings at booting?"
date: 2010-03-12
forum: Hardware
---

### Post by sideral on 2010-03-12
Hi

**The problem:**
When I boot ubuntu, it takes a lot of time in the logo screen (~2 minutes) then it reports a list of I/O errors, and finally it finishes booting and I get in. The problem doesn't happen always. 

**The details:**
I have a dual-booting setup with two hard disks, windows is in one (dev/sdb1), ubuntu is in the other. Apparently, the windows disk has bad sectors and Ubuntu is unable to mount it. I have run chkdsk from wiindows, but it doesn't seem to find any problem. I don't mind if Ubuntu can't read the disk, I just want those warnings to dissapear.

I am almost sure this disk is the source of the problem because, sometimes, Ubuntu is able to read it, and no errors are shown during boot when this happens.

[B]What I tried:
[/B]I tried to disabled automount by editing fstab. But Ubuntu seems to keep trying to read this disk on booting, even if it doesn't mount it. Disk Utillity is unable to read the disk as well, it can't even detect its filesystem. However, Windows doesn't complain.

[B]My request:
[/B]I just want ubuntu to completely ignore this disk. Any help would be greatly appreciated!

**/etc/fstab**
```
proc                                       /proc           proc         defaults                       0  0  
# Entry for /dev/sda2 :
UUID=b51b2839-6f3a-4617-a822-798f9d701df6  /               ext4         errors=remount-ro              0  1  
# Entry for /dev/sda5 :
UUID=06bc52cf-dc55-4e6f-b94e-d5eb0fcbc8c5  none            swap         sw                             0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8          0  0  
/dev/sdb1                                  /media/sdb1     ntfs         users,rw,noauto,noexec,umask=000    0  0  
/dev/sda1                                  /media/sda1     ntfs         nls=iso8859-1,users,umask=000  0  0
```

---

