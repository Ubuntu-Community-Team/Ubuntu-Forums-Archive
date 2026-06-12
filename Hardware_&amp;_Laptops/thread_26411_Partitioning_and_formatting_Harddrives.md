---
title: "Partitioning and formatting Harddrives"
date: 2005-04-12
forum: Hardware &amp; Laptops
---

### Post by Staesys on 2005-04-12
I recently replaced windows xp pro on my older desktop and while everything seems to be working alright...

I've read all of the posts regarding this subject, and honestly, nothing is working for me. Fdisk sees /dev/hdb as having three partitions (but when I try to fdisk /dev/hdb2 thru /dev/hdb3 it errors out, Cfdisk only see's one partition on each drive. In the device manager, it shows three volumes for the /dev/hdb drive. I'm having similar problems getting my  /dev/hdd1 working. I've tried partitioning and formating (fdisk, cfdisk, mkfs, etc...) multiple times, mounted them, put them in my /etc/fstab file and still I can't access them. They also don't show up in Places->Computer.

Is there anything I can to just wipe these drives and start over from scratch, or perhaps an easier and/or more reliable way of setting these harddrives up so I can use them in Ubuntu?

Here's my partition info and fstab:

Disk /dev/hdb: 2192 MB, 2192891392 bytes
255 heads, 63 sectors/track, 266 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         251     2016126   83  Linux
/dev/hdb2             252         266      120487+   5  Extended
/dev/hdb5             252         266      120456   82  Linux swap / Solaris

Disk /dev/hdd: 3216 MB, 3216310272 bytes
128 heads, 63 sectors/track, 779 cylinders
Units = cylinders of 8064 * 512 = 4128768 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1         778     3136864+   b  W95 FAT32

------------

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb1       /mnt/hdb1       ext3    defaults,errors=remount-ro 0       1
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd1       /mnt/hdd1       ext3    defaults,errors=remount-ro 0       1
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0
/dev/sdb        /media/usb1     auto    rw,user,noauto  0       0

---------------

Thanks in advance!

---

### Post by skoal on 2005-04-12
[QUOTE=Staesys] [...] when I try to fdisk /dev/hdb2 thru /dev/hdb3 it errors out[/QUOTE]

1. fdisk only accepts devices which refer to the *entire* disk (hdb), not any partitions (like hdb1, hdb2, etc.).  That's why you get those 'errors' when trying fdisk /dev/hdb1, etc.

2. Your disk information you provided seems incomplete/confusing and/or I'm missing something rather obvious in your '/etc/fstab' listing.

Can you post back with the output from:

> cat /proc/partitions

Give an overall picture of what *each* drive (and partition) is being used for (or how you wish to use it).

---

### Post by Staesys on 2005-04-12
major minor  #blocks  name

   3     0   39082680 hda
   3     1   38138278 hda1
   3     2          1 hda2
   3     5     939771 hda5
   3    64    2141495 hdb
   3    65    2016126 hdb1
   3    66          1 hdb2
   3    69     120456 hdb5
  22    64    3140928 hdd
  22    65    3136864 hdd1
 254     0   38138278 dm-0
 254     1     939771 dm-1
 254     2    2016126 dm-2
 254     3     120456 dm-3
 254     4    3136864 dm-4
   8     0      98304 sda
   8     4      98288 sda4
   8    16      16064 sdb
   8    17      15984 sdb1

---

### Post by Staesys on 2005-04-13
Thanks for your info about fdisk. I feel really silly now that it's so obvious.  :-) 

I was able to get the drives partitioned using hdb and hdd and used mkfs -t ext3 /dev/hdb1 (hdd1) to format them.

The problem is, now how do I access them? They're mounted at boot per /etc/fstab but they don't show up anywhere besides device manager.

Thanks!

---

### Post by skoal on 2005-04-13
It looks like you have:

hda drive (master), hdb drive (slave)
hdc cdrom (master), hdd drive (slave)
2 USB 'drive' mounts

and it's just hdb and hdd partitions that do not show up in Places > Computer?

If you open a terminal can you browse /mnt/hdb1 and /mnt/hdd1?  In other words, are they already mounted?  They should be already.

If so, then I think the issue is that you need to just make a 'symlink' in the /media directory to those two /mnt points.  That should make them visible in Gnome I think.

Example:

/media/hdb1 -> /mnt/hdb1
/media/hdd1 -> /mnt/hdd1

I'm not currently in Ubuntu or Gnome but I think this is how I did it in the past.  If that don't work, I think you need to set the Volume Visible flag in Nautilus (and I forget how to do that).

---

### Post by Staesys on 2005-04-13
root@ubuntu:/home/paul # /media/hdb1 -> /mnt/hdb1
bash: /mnt/hdb1: Is a directory
root@ubuntu:/home/paul # /media/hdd1 -> /mnt/hdd1
bash: /mnt/hdd1: Is a directory
root@ubuntu:/home/paul # ln -s /media/hdb1 /dev/hdb1
ln: `/dev/hdb1': File exists
root@ubuntu:/home/paul # ln -s /media/hdd1 /dev/hdd1
ln: `/dev/hdd1': File exists


When I browse to /mnt/hdb1 (hdd1) I see a "lost+found". When I use Places -> Computer and browse through the file system to the same place I see a folder with a red X on it and when I try to copy something to it I get a message that I don't have permissions to do that.

It's frustrating because I know I'm probably overlooking something basic, but as it says under my "Nick" I'm a newbie at lunux. Now if it where DOS or Windows I'd have no problem. lol

Thanks for all the help, it's appreciated!

-Paul

---

### Post by skoal on 2005-04-13
Staesys, it sounds to me like those 2 drives (in question) are already mounted and you can access them -> lost+found shows up.

In that case, just change the permissions on those drives as root (or by using sudo).

I don't know what you plan on using those drive/partitions for but just change the group ID on them (or even the user ID if you want).

I believe Ubuntu has a 'users' group.  I think I remember adding myself to it.  If you're not already part of that group, then:

sudo adduser <username> users

Then change the group ID on those drives (for example):

sudo chgrp users /mnt/hdb1
sudo chmod g+w /mnt/hdb1

* That should allow you to access those drives as normal user.  Hopefully that will send that annoying little red X back to /dev/null where it belongs.

---

### Post by Staesys on 2005-04-13
Well...  The good news is that with a **CHMOD A+RWX** I was able to gain access to the drives by browsing the filesystem to the /mnt directory, but they still don't show up in Gnome.

I'm using these drives to store some music files of mine.

:-)

-Paul

---

### Post by skoal on 2005-04-13
Yeah, sorry about that Staesys.  I'm no Gnome expert.  At the very least, you can browse to the /mnt folder now in Gnome and access it that way.  Right?  Unless the Gnome file manager was created by the RIAA, it should work hopefully.  The other possibility is changing the 'defaults' in fstab (for those 2 drives) to something else.  When I get my Gnome running and 2nd hard drive, I'll figure it out and pm you or post back here.

---

