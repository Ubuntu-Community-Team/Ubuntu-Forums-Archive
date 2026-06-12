---
title: "Can`t create partition on new SATA drives?"
date: 2009-12-31
forum: Hardware
---

### Post by shawnduncan on 2009-12-31
I just put two new SATA drives in. Ubuntu is installed on an older ata drive. 
The disk utility in administration sees them but when I try to create a partition, I get this error message: "One or more block devices are holding /dev/mapper/sil_afbhdccfbhag".

It also lists four drives when there is only two?

Is there something I`m missing?
Thanks.

---

### Post by shawnduncan on 2009-12-31
Now I`m really confused. After restarting machine it now shows three drives?

---

### Post by IcarusR on 2009-12-31
Used gparted, drives must be unmounted first.

---

### Post by oldfred on 2009-12-31
Were these drives ever in a raid configuration. I know you said they were new, but raid settings can cause confusion.

---

### Post by shawnduncan on 2009-12-31
IcarusR, Installed gparted. The unmount option is greyed out and it also sees three drives? When I tried to create a partition, I got this error message:GParted 0.4.5

Libparted 1.8.8.1.159-1e0e
Create Primary Partition #1 (ext2, 114.49 GiB) on /dev/sda  00:00:02    ( ERROR )
     	
create empty partition  00:00:01    ( SUCCESS )
     	
path: /dev/sda1
start: 63
end: 240107489
size: 240107427 (114.49 GiB)
set partition type on /dev/sda1  00:00:01    ( SUCCESS )
     	
new partition type: ext2
create new ext2 file system  00:00:00    ( ERROR )
     	
mkfs.ext2 -L "storagea" /dev/sda1
     	
mke2fs 1.41.9 (22-Aug-2009)
/dev/sda1 is apparently in use by the system; will not make a filesystem here!

OldFred, These drives were briefly part of a mirror. Is there something I should have done?

I`ve attached a pic of gparted`s window. sda and sdb are the drives in question. Not sure what mapper/sil_afbhdccfbhag is though?

---

### Post by oldfred on 2009-12-31
See this post and try this if sda & sdb or renumber as they are:
Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb

---

### Post by shawnduncan on 2009-12-31
OldFred,
Thanks so much for the help!
Followed the link, thanks! Getting closer I think. The strange third drive is now gone but still can`t create a partition on either drive.
Now gparted give this error message:
GParted 0.4.5

Libparted 1.8.8.1.159-1e0e
Create Primary Partition #1 (fat32, 114.49 GiB) on /dev/sda  00:00:01    ( ERROR )
     	
create empty partition  00:00:00    ( SUCCESS )
     	
path: /dev/sda1
start: 63
end: 240107489
size: 240107427 (114.49 GiB)
set partition type on /dev/sda1  00:00:01    ( SUCCESS )
     	
new partition type: fat32
create new fat32 file system  00:00:00    ( ERROR )
     	
mkdosfs -F32 -v -n "storagea" /dev/sda1
     	
mkdosfs 3.0.3 (18 May 2009)
mkdosfs: unable to open /dev/sda1

---

### Post by shawnduncan on 2009-12-31
BINGO!

Being in a rush all the time, I did`nt restart machine after following the link you posted.
All is right with the world again.
Thanks!!!

---

