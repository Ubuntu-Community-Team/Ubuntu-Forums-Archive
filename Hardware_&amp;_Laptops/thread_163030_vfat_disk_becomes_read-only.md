---
title: "vfat disk becomes read-only"
date: 2006-04-20
forum: Hardware &amp; Laptops
---

### Post by calagan on 2006-04-20
One of the vfat partitions of my IDE internal HDD has suddenly become read-only.

Any attempt at creating or deleting a file or folder results in the same error message: "cannot ...: Read-only file system"

Here's a dump of my /etc/fstab file: 

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /big            vfat umask=000 0 0
/dev/hda2       /big2           vfat umask=000 0 0
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

The problem is occuring on the "/big" partition and although "/big2" is configured exactly the same way, it remains writeable.

I tried to reload fstab with "mount -a" and also a couple of reboots (you know, good old Windows admin habit...), but this didn't help.

This may or may not be relevant, but I have [TorrentFlux 2.1 ]("http://torrentflux.com")installed using "/big" as its download folder.

Thanks in advance for your help.

Cal
- Ubuntu 5.10
- Python 2.4.2
- PHP 5.0
- Apache 2.0

---

### Post by Tom Tiger on 2006-04-20
mm... it seems your fstab needs some extra work,

you could try the following line for your big and big2 drives

/dev/hda1       /mnt/big        vfat     user,auto,rw,exec,users 0     0
/dev/hda2       /mnt/big2       vfat     user,auto,rw,exec,users 0     0

with a bit of luck this will work :-)  I'm using this to acces my usb harddrive

---

### Post by ruzle0 on 2006-04-20
i had a smilar problem with my fat partition becoming read only, my fstab options are the same as you posted for vfat. 
i was also using using a torrent client at the time the error would occur[although i don't use the partition much so it may not be related]
if you ```
sudo umount /dev/hda1 
and then 
sudo mount /dev/hda1
``` you should be able to write to it again.
i have also noticed with ```
dmesg
``` that there are kernel panic messages relating to the partition once the partition has become RO. This error has stopped now, [possibly as i have more data on the drive, so i think there may have been a problem with writing to a portion of the partition and turning read only is a protection.]
if i get the error recuring i willl run some kind of drive fitness test over the disk/partition. 
if you find anything else out yourself please update the thread as i'd be interested too.

---

### Post by calagan on 2006-04-22
Thanks for your help, ruzle0's solution did the trick, but I have to say it was a scary experience not to be able to write to those partitions for couple of days. Turning those partition to ext3 is in my top priorities, or maybe XFS...

---

### Post by hellmet on 2007-06-30
I've the same problem with my Azurues.

---

