---
title: "drive not detected by apps"
date: 2008-12-29
forum: Hardware
---

### Post by dehog on 2008-12-29
I m on a dual boot with Windows XP.
In Ubuntu I can access my drives (mount/unmount/read/write), but the applications, for example Amarok, cannot see these drives (All of them NTFS).

I tried automatically mounting particular drives with "NTFS Configuration Tool", but I get this error 

```

Error : An Error occured when trying to configure /media/media, please retry. Thanks.

```

When I see the permissions on the drives I get this message:
```

The Permission of "Drive name" could not be determined

```

How should I fix this.

P.S: Rebooting into Windows and back doesn't fix this !

Thanks

---

### Post by ajgreeny on 2008-12-29
You can edit your /etc/fstab file manually to get the ntfs drive/partition to mount at boot time, then your files will be seen by the applications as */media/WindowsXP/path/to/file.*

Firstly, if it does not already exist, make a mount point with ```
sudo mkdir /media/WindowsXP
```
Now use ```
gksudo gedit /etc/fstab
``` to edit the fstab file and add this line to the file
```
/dev/sda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
```changing the dev name for windows to your setup, probably /dev/sda1, but check that with ```
sudo fdisk -l
``` first.  Good luck.

---

