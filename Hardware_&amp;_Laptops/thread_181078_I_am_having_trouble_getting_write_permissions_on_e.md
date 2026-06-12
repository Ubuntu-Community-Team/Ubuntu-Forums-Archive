---
title: "I am having trouble getting write permissions on external hard drive and flash drive."
date: 2006-05-23
forum: Hardware &amp; Laptops
---

### Post by glassgloss on 2006-05-23
any ideas?

What do you need to know to help me?

the media mounts fine, ubuntu recognizes it and can read it, I just cannot write to it.

---

### Post by aysiu on 2006-05-23
Can you plug the drive in and then post here the output of these terminal commands? ```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

### Post by glassgloss on 2006-06-09
glassgloss@glassgloss:~$ sudo fdisk -1
Password:
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
glassgloss@glassgloss:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              18G   13G  3.8G  78% /
varrun                252M   68K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  116K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   19M  234M   8% /lib/modules/2.6.15-23-386/volatile
/dev/sdb1             233G   12G  222G   6% /media/LACIE
glassgloss@glassgloss:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
glassgloss@glassgloss:~$

---

### Post by aysiu on 2006-06-09
That's an -l, as in the letter L, not the number one: -1.

---

### Post by spazsui on 2006-07-02
I am also having the same problem with my external firewire drive.  Ubuntu dapper mounts it and recognizes it.  I can open it and look at the contents but I can't modify anything ( delete files or add files ).  I don't have permissions to write to it.  I saw this post and was hoping you can help me.  I am a total newb to Ubuntu.  Here is my info that you requested from the previous poster who started this thread.  Thanks for any help.:-? 


Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14417   115804521   83  Linux
/dev/hda2           14418       14593     1413720    5  Extended
/dev/hda5           14418       14593     1413688+  82  Linux swap / Solaris

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         131     1052226   82  Linux swap / Solaris
/dev/sda2   *         132       19457   155236095   83  Linux

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             109G  5.4G   98G   6% /
varrun                236M   88K  236M   1% /var/run
varlock               236M  4.0K  236M   1% /var/lock
udev                  236M  128K  236M   1% /dev
devshm                236M     0  236M   0% /dev/shm
lrm                   236M   18M  218M   8% /lib/modules/2.6.15-25-k7/volatile
/dev/sda2             149G   33M  149G   1% /media/ieee1394disk

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by aysiu on 2006-07-02
Based on what I see, it looks as if it's /dev/sda2 that you're trying to mount with the correct permissions. Since it's a Linux partition, though, the problem probably lies in the *file* and *folder* permissions instead of the mounting parameters.

Try this: ```
sudo chown -R spazsui:spazsui /media/ieee1394disk
sudo chmod -R 755 /media/ieee1394disk
```

---

### Post by spazsui on 2006-07-04
Thanks!  That's seems to work!  Do I have to go into the terminal each time and type that command each time I want to save a file to the external hard drive or will it work always from now on?  Also, I reformatted the drive through Ubuntu, does that mean it is no longer a fat32?  I want to be able to use this drive along with a windows computer so do I have to reformat again with fat32?  As you can tell I am extremely new to Linux and Ubuntu in general so if any of my questions are elementary I do apologize.  I appreciate all help that is given.  Thanks for all of your patience!

---

### Post by spazsui on 2006-07-04
If I reformat as a fat32 does that mean the command I would type in the terminal now change?  If so, what would it be now?:-s

---

### Post by aysiu on 2006-07-05
You can read/write Ext3 partitions from Windows with this driver:
[http://www.fs-driver.org](http://www.fs-driver.org)

If you reformat as FAT32, follow these directions to mount it:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Gigidy5 on 2008-02-09
k here is the info...



Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7296    58605088+   7  HPFS/NTFS


k then,
do i try the fs driver thing or what?




thanks... i know this is pretty much dead (the post) but thanks for the help:)

---

