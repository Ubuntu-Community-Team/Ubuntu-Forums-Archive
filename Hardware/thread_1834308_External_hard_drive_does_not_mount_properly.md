---
title: "External hard drive does not mount properly??"
date: 2011-08-27
forum: Hardware
---

### Post by pedro_miguel on 2011-08-27
Hi there guys;
I need help with something, I've moved to Ubuntu in the last few days (thats why  this stupid question) and deleted windows for good(i was tired of it)  but i have this wd external hard drive with 500gbytes that refuses to  mount : ) i know that there are loads of tutorials on how to do it but i  just don't want to loose everything i have inside the hard disk the  error i get is the following: 

```
Error mounting: mount exited with exit code 12: Failed to read last sector 
(976771119): Invalid argument HINTS: Either the volume is a RAID/LDM but it wasn't setup 
yet, or it was not setup correctly (e.g. by not using mdadm --build ...),   
or a wrong device is tried to be mounted,    or the partition table is corrupt 
(partition is smaller than NTFS),    or the NTFS boot sector is corrupt (NTFS size is 
not valid). Failed to mount '/dev/sdc1': Invalid argument The device '/dev/sdc1' doesn't
seem to have a valid NTFS. Maybe the wrong device is used? Or the whole disk instead
of a partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
```The output of sudo fdisk -l is the following:

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00046017

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9470    76062720   83  Linux
/dev/sda2            9470        9730     2085889    5  Extended
/dev/sda5            9470        9730     2085888   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500105740288 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00029d3c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60802   488385560    7  HPFS/NTFS
```I also followed the example to mount a external hard drive given on Ubuntu documentation [https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB) so this was what i did: 

```
pedro@pedro-HP-Pavilion-dv1000-EF025EA-AB9:~$ sudo mkdir /media/external
pedro@pedro-HP-Pavilion-dv1000-EF025EA-AB9:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/external
```after pressed enter i received this

```
Failed to read last sector (976771119): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
```
So i'm a bit lost now any ideas please...can anyone tell me what i'm i doing wrong or explain me how to do it properly.....thanks for your time guys.

---

### Post by oldfred on 2011-08-27
Did you create a windows repairCD before you deleted Windows so you can maintain your NTFS partitions? Linux can repair many issues in windows, but cannot run chkdsk and sometimes cannot repair partition boot sector (PBR) which must have a NTFS signature.

You can use just about any windows repairCD to run chkdsk. I just used a Win7 repairCD to fix my XP but then had to reload NTFS  PBR as it converted from XP to Vista/7 type.

Vista/7 CHKDSK
chkdsk [drive] /f /r
chkdsk C: /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. Rerun until no errors.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by pedro_miguel on 2011-08-27
Actually no i did not created a windows repair cd before the windows deletion, so what now do i need to re-install windows and create a windows repair cd or should i just type on terminal what you've wrote:  
> chkdsk [drive] /f /r
chkdsk C: /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you  specify the chkdsk command without arguments, the command checks the  current drive with no options in effect. Rerun until no errors.

hmmm still a bit confuse sorry.

---

### Post by oldfred on 2011-08-27
chkdsk is a windows only command.

Linux NTFS tools has ntfsfix but it only repairs minor things and sets the chkdsk flag, so on next reboot of windows chkdsk is automatically run. But Ubuntu will not mount a NTFS partition with the chkdsk flag set, to prevent damage that chkdsk may then not be able to fix.

If you know anyone with windows.

Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

You used to be able to download a repair only ISO that let you fix Vista or 7 and that is what I used to fix my XP. But it is not available anymore. Check with your computer vendor or others to see if you can get a repairCD.
When I tried Google before, just about everyone linked back to the neosmart site and they are saying due to copyright issues they cannot provide the repairCD anymore.

---

### Post by tijgertje on 2011-08-27
> **oldfred said:**
> But Ubuntu will not mount a NTFS partition with the chkdsk flag set, to prevent damage that chkdsk may then not be able to fix.

 It is posible to mount dirty filesystems (mount --force) **but** you risk permanent damage to the files.  Cleaning the filesystem with a windows cd (any will do) is the best option. reinstalling windows is not nessesary.  And when you have the files from that disk backupt format it with a proper FS like ext3/4

---

