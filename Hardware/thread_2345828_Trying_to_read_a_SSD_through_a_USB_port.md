---
title: "Trying to read a SSD through a USB port"
date: 2016-12-08
forum: Hardware
---

### Post by old_dog on 2016-12-08
The title says it all really, 14.04 Ubuntu.
Two questions 
1) should I be able to do this ?

2) got this error message.... What do I do next? The disk to come out of earlier version of 14.04 if that helps what do I do next

Error mounting /dev/sdg2 at /media/percy/0E3E52833E52642D: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sdg2" "/media/percy/0E3E52833E52642D"' exited with non-zero exit status 12: Failed to read last sector (117223423): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sdg2': Invalid argument
The device '/dev/sdg2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

---

### Post by oldfred on 2016-12-08
Since drive is NTFS, was it used with Windows 8 or later?

If so did you turn off fast boot or the always on hibernation?
The Linux NTFS driver will not mount NTFS that is hibernated or if it needs chkdsk. That is to prevent damage.

You may be able to mount read only. But should boot Windows and turn off fast start or hibernation. 
Read only mount of Windows may work if corrupted or hibernated replace sda# with correct drive.
sudo mkdir /mnt/win
sudo mount -o ro /dev/sda# /mnt/win 

 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 

 [http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)

---

