---
title: "mounting a XP HDD"
date: 2012-07-08
forum: Hardware
---

### Post by gengoro on 2012-07-08
Hi all, 

  I am trying to add my XP hdd to my fstab, but the file system is showing up as unallocated in gparted.  At one point, I had a dual boot going with the drive... but removed linux.  I am not sure how to make this drive recognizable again (without formatting).  If anyone has any ideas, please let me know.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb633b633

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?           1       30401   244187984+   7  HPFS/NTFS
/dev/sda2           30401       60801   244196016+   f  W95 Ext'd (LBA)
/dev/sda5           30401       60801   244195985    7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005b455

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4661    37431296   83  Linux
/dev/sdb2            4661        4866     1648641    5  Extended
/dev/sdb5            4661        4866     1648640   82  Linux swap / Solaris



ginnai@ginnai-desktop:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2012-07-08 20:27 699bd890-90cc-49de-b227-7da7071de809 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2012-07-08 20:27 a1c6bc17-b57e-499d-ae2d-582857eba541 -> ../../sdb5



ginnai@ginnai-desktop:~$ sudo lshw -C disk
  *-cdrom                 
       description: DVD-RAM writer
       product: CDDVDW SH-S223Q
       vendor: TSSTcorp
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: SB03
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc
  *-disk
       description: ATA Disk
       product: WDC WD5001AALS-0
       vendor: Western Digital
       physical id: 1
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 01.0
       serial: WD-WCASY3884138
       size: 465GiB (500GB)
       configuration: ansiversion=5 signature=b633b633
  *-disk
       description: ATA Disk
       product: ST340014A
       vendor: Seagate
       physical id: 0.1.0
       bus info: scsi@6:0.1.0
       logical name: /dev/sdb
       version: 3.54
       serial: 5JV90SPT
       size: 37GiB (40GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0005b455

Can't think of any other outputs that could help, but just let me know!  Thanks for any ideas.

---

### Post by oldfred on 2012-07-08
It is saying there is some error on partition table. The ? should either be * for boot flag or blank. Not sure if something else. Linux will often not mount NTFS partitions that need chkdsk, so try running chkdsk on sda1 & sda5. Probably c: & d: in Windows. You may have to run from a Windows repairCD or your XP install disk.

I have used a Windows 7 repairCD to run chkdsk on my XP install but then also had to rewrite the NTFS partition boot sector as it converted it to Windows 7 and it needed to be XP.

XP CHKDSK command:
chkdsk drive /p /r
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information. Run chkdsk several times, until no more errors are detected.
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by gengoro on 2012-07-09
I just ran chkdsk and errors were corrected, but I have still been unable to mount the drive. I attempted to add the drive to the fstab, but still no dice. This is my first time in fstab, so its possible that I made a mistake. 

/dev/sda  /media/windows  auto	rw/use,noauto,exec	0	0

I made the media/windows directory beforehand, but I am too new to know this is correct. Can you suggest anything?

---

### Post by ahallubuntu on 2012-07-09
Don't worry about fstab until you figure out how to mount the partition manually.

You have two NTFS partitions, /dev/sda1 and /dev/sda5 .  Which one are you trying to mount?

Create the mount directories first:

```
sudo mkdir /mnt/sda1
sudo mkdir /mnt/sda5

```

then can you do either of these:

```
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sda5 /mnt/sda5
```

?

If you can't, something is still corrupted and no fstab entry will work.

---

### Post by oldfred on 2012-07-09
Sometimes chkdsk needs to be run until there are no errors as it does not fix everything on one pass.

ahallubuntu's suggestion is a good way to test if you can mount them. Nautilus should also auto mount the NTFS partitions if they are ok, also.

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

Unmount if manually mounted or mounted with Nautilus first or it will not mount a second time.
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
# Anytime you edit fstab always do this before rebooting. If no errors it just remounts everything, but if errors you have to fix before rebooting or you may not be able to:
sudo mount -a

example NTFS from Morbius1, change example UUID to yours
To see UUIDs which are prefered over device like /dev/sda1
sudo blkid
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
suggest using templates instead. Post #6
For ntfs, you can use any name you like instead of WinD or sda1:
sudo mkdir /media/WinD
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

---

