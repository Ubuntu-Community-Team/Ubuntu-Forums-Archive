---
title: "partion and mount trouble"
date: 2007-08-19
forum: Hardware &amp; Laptops
---

### Post by robert.cooper on 2007-08-19
using gpart, i formatted an ext3 part. i can't write to it however. "info" says it's unmounted, while  my right click options reveal only an option to "unmount".
what should i do?
i have ~117gb free, and want to use 80 or so of it for my flac music collection. i used a fat32 part for a while for vista-conversion/moving, but apparently, those max at 30gbs...
should i try an ext2 part?

---

### Post by merlinus on 2007-08-19
Post results of:

```

sudo fdisk -l
mount
cat /etc/fstab

```

-merlin

---

### Post by robert.cooper on 2007-08-19
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1946    15631213+  83  Linux
/dev/sda2            1947        2189     1951897+  82  Linux swap / Solaris
/dev/sda3   *        2190        4484    18432000    7  HPFS/NTFS
/dev/sda4            4485       15320    87040170    5  Extended
/dev/sda5            4485       15320    87040138+  83  Linux
robert@robert-laptop:~$

---

### Post by merlinus on 2007-08-19
Is sda5 the partition in question?

Also, post results of these, entered one at a time:

```

mount
cat /etc/fstab

```

-merlin

---

### Post by robert.cooper on 2007-08-19
i tried to do an ext2, but now gnome part editor wont show anything...

robert@robert-laptop:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/dev/sda3 on /media/sda3 type ntfs (rw,nls=utf8,umask=007,gid=46)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
robert@robert-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4cb38b56-8168-447b-933a-2e633bb1ebd1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=8B7A-0C8F  /fat32          vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=6A54297854294861 /media/sda3     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=92f60477-4d2c-46ea-875f-ea243c65b03b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
robert@robert-laptop:~$

---

### Post by merlinus on 2007-08-19
Once again, is sda5 the partition in question?  If so, it is listed as fat32 in /etc/fstab, which is incorrect, according to what you have posted.

ext3 is a better filesystem than ext2, and is not the reason you are having mounting problems.

So I recommend using gparted live cd to get to your partitions, and perhaps change them:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

After you are satisfied with the partitions and filesystems, post the output of those three commands again, and add one more:

```

blkid

```-merlin

---

### Post by robert.cooper on 2007-08-19
thanks for the help. i opened gparted to find that nothing was recognized on my drive, so im redoing ubuntu now, and have used all space on my drive now, so hopefully there wont be any more problems. let this be a lesson; don't sit on the fence!; pick ubuntu or windows!
most importantly, however, i need to know how to import audio cds. ive posted in the right folder for it (sound/video) but i havent had a response yet. ive recently converted my aif and mp3 collection to flac, to find my meta data gone. so now i think ill just request all the old cds (and many new ones) from the library again. no more windows! if flac becomes obsolete i swear to whatever i most strongly believe in that i will kill someone. anyway, i am in fact, very passionate about my music collection; i'm an avid classical music fan and aside from that, i mostly just do web browsing,,, ubuntu is a window into the confusing world of command line, and i'm trying to learn as much as i can (mostly by copying and pasting :)

---

### Post by merlinus on 2007-08-19
A suggestion, since you are using your entire hdd for ubuntu.

You may wish to create a separate /home partition, for storing your music.  It is also where preferences, bookmarks, configurations, email, etc. are kept.

Then when reinstalling or upgrading, that partition will remain intact.

More info here:

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

-merlin

---

