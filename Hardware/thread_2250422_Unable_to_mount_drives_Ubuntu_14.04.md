---
title: "Unable to mount drives Ubuntu 14.04"
date: 2014-10-28
forum: Hardware
---

### Post by oquadros on 2014-10-28
Hey guys,

I have three hard drives in my computer, each 1TB, one from building the computer and the other two salvaged from externals. Anyway, I have Ubuntu 14.04 installed on one HDD, Windows 8.1 on another, and the last one is just a file storage one (TwinTurbo).

So i am having the issue that when i try to mount either the windows drive or the storage drive while on Ubuntu, It gives me the following message:

> Error mounting /dev/sda1 at /media/oliver/TwinTurbo: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sda1" "/media/oliver/TwinTurbo"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda1': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.


Do you guys have any idea what could be the problem? I have logged into the windows HDD and shut down completely but still get the same message. Any help would be great!

---

### Post by yancek on 2014-10-28
> The disk contains an unclean file system (0, 0).

If you did a clean/complete shutdown rather than hibernate, you might need to run chkdsk from windows.  Some info on it from the microsoft site:

[http://technet.microsoft.com/en-us/magazine/ee872425.aspx](http://technet.microsoft.com/en-us/magazine/ee872425.aspx)

---

