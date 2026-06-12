---
title: "Problem with external hdd: no desktop icon"
date: 2016-02-27
forum: Hardware
---

### Post by marsdenf on 2016-02-27
Using Xubuntu 14.04.  There is no desktop icon for my seagate 1Tb external hard drive when I plug it in.  This is definitely a problem with the drive itself, and not with xubuntu.  Disks utility recognizes the drive but thunar does not.  After mounting the drive with disks utility, I can access the files on it, and thunar shows the drive.  Even after mounting, there is no desktop icon.  Rebooting with the drive plugged in etc makes no difference.  Here is the output of lsusb -D :  (I don't know if there is supposed to be a space after -D)


           marsdenf@marsdenf-Z170X-Gaming-3:~$ lsusb -D /dev/sdd
Cannot open /dev/sdd
marsdenf@marsdenf-Z170X-Gaming-3:~$ lsusb -D/dev/sdd
Cannot open /dev/sdd
marsdenf@marsdenf-Z170X-Gaming-3:~$ lsusb -D /dev/sdd1
Cannot open /dev/sdd1
marsdenf@marsdenf-Z170X-Gaming-3:~$ lsusb -D/dev/sdd1
Cannot open /dev/sdd1
marsdenf@marsdenf-Z170X-Gaming-3:~$ 

 After the drive is mounted using disks, the output is the same. (The drive is identified in disks as /dev/sdd  and /dev/sdd1).  Here is info from disks:

          model: Seagate FA GoFlex Desk (0155)
          size:    1.0 TB (1,000,204,885,504 bytes)
          partitioning:  Master Boot Record "
          serial no.:  NA0J7SHG
          device:  /dev/sdd1
          partition type:  0x00
          contents: FAT(32bit version)   (My computer is 64 bit)

Disks utility show two volumes, one called EXT_HDD  Partition1 1.0TB FAT and another called free space (2.6 mb)  (EXT_HDD is the name I gave the drive)
In "disks utility"-"more actions"-"edit mount options"  automatic mount options are on and the rest is shaded out.  ("show in user interface" is checked but shaded out)
I tried turning off automatic mount options, and experimenting with different "Identify as" options, and then a desktop icon appeared.  But if I tried to mount the device using the icon, I got an error message "only root can mount ...etc".
Trying to mount the device using disks gave this error message:

      Error mounting filesystem
      Error mounting system-managed device /dev/sdd1: Command-line `mount "/mnt/usb-Seagate_FA_GoFlex_Desk_NA0J7SHG-0:0-part1"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

 (udisks-error-quark, 0)
           
  This happened no matter which "identify as" options I chose.  When I bought the drive, it had some windows programs and other files on it.  I removed those files (copied them to my desktop comp, I still have them) and got instructions on a newsgroup on how to format the drive using the command line.  Must have made a mistake in this.  Anyone know how to fix this drive so it will work properly?

---

### Post by marsdenf on 2016-02-27
I tried again using " LABEL=EXT_HDD " for "identify as" in "edit mount options" and then a desktop icon appears, and thunar recognizes the drive, even though it is unmounted. But if I try to mount the drive using the icon, I get the "only root can mount..." error msg.  But I can mount the drive using disks utility, but then the icon does not recognize that the drive is mounted.  "Require additional authorization to mount" is UNchecked.  There is an unlabelled line in "mount options"  with these words:

nosuid,nodev,nofail,noauto,x-gvfs-show

UPDATE: I added " users, " to the line: "  LABEL=EXT_\040HDD /mnt/EXT_\040HDD auto users,nosuid,nodev,nofail,noauto,x-gvfs-show 0 0  "  in etc/fstab.   Now when I try to mount the drive using the icon, I get the error msg:  failed to mount EXT_HDD  mount: mount point /mnt/EXT_ HDD does not exist  .    I also noticed that when I use disks utility to mount the drive, it creates a second entry for the drive in thunar.  In /mnt  there is an empty folder named "  EXT_\x20HDD  ".   Since in the line in fstab the drive is labeled "   EXT_\040HDD  ",  I tried renaming the folder in /mnt to "  EXT_\x40HDD  " but the same error message appeared.  I also created a folder in /mnt called EXT_HDD  but that didn't work.  I don't really know anything about these things, I am just fooling around.  (Yes, I know it is dangerous)

UPDATE:  In "  edit mount options  "  tried  "  identify as:  "  /dev/disk/by-label/EXT_\x020HDD  "  and then there is an icon on the desktop, and thunar recognizes the unmounted drive, but when I try to mount the drive using disks utility, get the error msg: 


             Error mounting filesystem
                          Error mounting system-managed device /dev/sdd1: Command-line `mount "/mnt/EXT_\\x20HDD"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

 (udisks-error-quark, 0)

and when trying to mount using desktop icon or thunar, this error:

Failed to mount "EXT_\x20HDD"
mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I am beginning to suspect that the problem may be the name I gave the drive, ie the underscore.

Here is the output of dmesg | tail  :

         marsdenf@marsdenf-Z170X-Gaming-3:~$ dmesg | tail
[ 2750.853233] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:c8:fb:26:55:eb:fc:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
[ 2877.930691] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:c8:fb:26:55:eb:fc:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
[ 3005.068069] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:c8:fb:26:55:eb:fc:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
[ 3131.890602] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:c8:fb:26:55:eb:fc:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
[ 3136.359414] FAT-fs (sdd1): Unrecognized mount option "x-gvfs-show" or missing value
[ 3208.086678] FAT-fs (sdd1): Unrecognized mount option "x-gvfs-show" or missing value
[ 3259.013002] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:c8:fb:26:55:eb:fc:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
[ 3284.948714] FAT-fs (sdd1): Unrecognized mount option "x-gvfs-show" or missing value
[ 3385.940395] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:c8:fb:26:55:eb:fc:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
[ 3513.147716] [UFW BLOCK] IN=eth0 OUT= MAC=01:00:5e:00:00:01:c8:fb:26:55:eb:fc:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
marsdenf@marsdenf-Z170X-Gaming-3:~$

UPDATE: Solved.   by changing "  x-gvfs-show  "  in the line in fstab for the drive to  "  comment=x-gvfs-show  "   the problem is completely solved.   I got this from a thread in ask ubuntu.

---

