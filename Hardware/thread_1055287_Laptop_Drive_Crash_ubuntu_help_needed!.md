---
title: "Laptop Drive Crash ubuntu help needed!"
date: 2009-01-30
forum: Hardware
---

### Post by choirman on 2009-01-30
My Dell Inspiron 6000 crashed it's hard drive - and I need help getting access to my files.  A friend told me about Ubuntu, and I have a disc and instructions.  When I start it (without making changes to my computer), it starts fine.  I go to Places/Computer - hoping to at least be able to see my hard drive so I can either open it up or get an error message while trying to open it up so I know how to try to fix it.  INSTEAD - all it shows is my CD-ROM drive and Filesystem - no additional drives.  Can you help me gain access to it so I might be able to mount the drive?:(

---

### Post by taurus on 2009-01-30
First, does the BIOS even detect your harddrive?  If it doesn't then Ubuntu won't either.

But if the BIOS detect your harddrive, then boot Ubuntu LiveCD.  Open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -**l**
```
That is a lower case letter L, not number 1.

---

### Post by choirman on 2009-01-30
Thanks for replying!
I don't have the computer hooked up to the net - so I don't know how to easily copy and paste.  I did run the command - what am I looking for (or tell me how I cna quickly copy and paste to you).

---

### Post by choirman on 2009-01-30
Here are the results: (I connected on my broke laptop...)

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8        6827    54781650    7  HPFS/NTFS
/dev/sda3            6828        7295     3759210   db  CP/M / CTOS / ...
ubuntu@ubuntu:~$

---

### Post by taurus on 2009-01-30
I assume /dev/sda2 is the partition you want to get access to.  From a terminal, see if you can mount it with the force option.

```
sudo mkdir /media/sda2
sudo mount -t ntfs-3g /dev/sda2 /media/sda2 -o force
df -h
```

---

### Post by choirman on 2009-01-30
This is what I got:

ubuntu@ubuntu:~$ sudo mkdir /media/sda2
ubuntu@ubuntu:~$ sudo mount -t ntfs-3g /dev/sda2 /media/sda2 -o force

$MFT has invalid magic.
Failed to load $MFT: Input/output error
Failed to mount '/dev/sda2': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.
ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                1009M  2.0M 1007M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                1009M  2.0M 1007M   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                1009M     0 1009M   0% /lib/init/rw
varrun               1009M  108K 1009M   1% /var/run
varlock              1009M     0 1009M   0% /var/lock
udev                 1009M  2.8M 1006M   1% /dev
tmpfs                1009M  244K 1008M   1% /dev/shm
rootfs               1009M  119M  890M  12% /
/dev/scd0             699M  699M     0 100% /cdrom
/dev/loop0            676M  676M     0 100% /rofs
tmpfs                1009M   28K 1009M   1% /tmp
/dev/mmcblk0p1        489M  399M   90M  82% /media/disk
ubuntu@ubuntu:~$

---

### Post by taurus on 2009-01-30
Maybe one of these threads helps.

[http://ubuntuforums.org/search.php?searchid=55107731](http://ubuntuforums.org/search.php?searchid=55107731)

---

