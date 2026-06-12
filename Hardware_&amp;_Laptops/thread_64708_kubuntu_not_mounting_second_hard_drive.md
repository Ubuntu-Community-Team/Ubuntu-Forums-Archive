---
title: "kubuntu not mounting second hard drive"
date: 2005-09-11
forum: Hardware &amp; Laptops
---

### Post by mcndjxlefnd on 2005-09-11
I just installed kubuntu on my computer and almost everything works fine.  I reformatted one hardrive and installed kubunto on that drive.  I have a second drive, formatted ntfc by windows, that has media files I would like to access.  Kubuntu won't mount the drive and i don't want to have to erase my files.

---

### Post by codejunkie on 2005-09-11
[QUOTE=mcndjxlefnd]I just installed kubuntu on my computer and almost everything works fine.  I reformatted one hardrive and installed kubunto on that drive.  I have a second drive, formatted ntfc by windows, that has media files I would like to access.  Kubuntu won't mount the drive and i don't want to have to erase my files.[/QUOTE]
use ```
sudo fdisk -l
``` find the location of the drive for example /dev/hdb1 and then follow one of these guides to mount that drive
[http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows) that should do it but never write data to a ntfs drive from linux it can corrupt the data only read data from it.
edit: also the steps in that guide were written for gnome not kde so when a step says to use "gedit" which is just a text editor for gnome substitute it for "kate" or "kwrite" the text editors for kde that should do the same thing hope this helps.

---

### Post by Benzima on 2005-09-11
I have the exact same problem. Been trying to find the answer for myself all day. I posted almost the exact same question, but I accidently but it in th 5.10 preview section.

[http://www.ubuntuforums.org/showthread.php?t=64632](http://www.ubuntuforums.org/showthread.php?t=64632)

My slave drive shows up in Device Manager but not in Places/Computer. Is that normal? Does the above solution fix that problems too or is that somethnig different?

Here's what I get:

*****
benzima@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 20.5 GB, 20525137920 bytes
255 heads, 63 sectors/track, 2495 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2389    19189611   83  Linux
/dev/hda2            2390        2495      851445    5  Extended
/dev/hda5            2390        2495      851413+  82  Linux swap / Solaris

Disk /dev/hdb: 13.6 GB, 13601193984 bytes
255 heads, 63 sectors/track, 1653 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        1652    13269658+   7  HPFS/NTFS
benzima@ubuntu:~$ sudo mkdir
mkdir: too few arguments
Try `mkdir --help' for more information.
benzima@ubuntu:~$ sudo mkdir
mkdir: too few arguments
Try `mkdir --help' for more information.
benzima@ubuntu:~$ sudo mount /dev/hda1 /media/windows/ -t vfat -o iocharset=utf8,umask=000
mount: /dev/hda1 already mounted or /media/windows/ busy
mount: according to mtab, /dev/hda1 is mounted on /
benzima@ubuntu:~$ sudo mount /dev/hdb1
mount: can't find /dev/hdb1 in /etc/fstab or /etc/mtab
benzima@ubuntu:~$ sudo /dev/hdb1 -t ntfs -0 nls=utf8,umask=0222
sudo: /dev/hdb1: command not found
benzima@ubuntu:~$
*****

Any ideas?

---

### Post by codejunkie on 2005-09-11
[QUOTE=Benzima]I have the exact same problem. Been trying to find the answer for myself all day. I posted almost the exact same question, but I accidently but it in th 5.10 preview section.

[http://www.ubuntuforums.org/showthread.php?t=64632](http://www.ubuntuforums.org/showthread.php?t=64632)[/QUOTE]
posted solution in the link you provided, if you have any problems getting it to work  just let me know by PM or posting in that thread.

---

