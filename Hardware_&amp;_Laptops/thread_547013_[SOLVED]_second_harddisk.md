---
title: "[SOLVED] second harddisk"
date: 2007-09-09
forum: Hardware &amp; Laptops
---

### Post by Ampi on 2007-09-09
I have two harddisks, one with fedora and one with ubuntu. Ubuntu is the newest one which I want to use as my default, fedora just for storage. 

When I start fedora I can mount the ubuntu-disk without any problems, but when I start ubuntu, the fedora-disk is recognized but after mounting I only see the directories Grub adn Lost&Found, but where is my home folder??

I have fedora on my primary master (hda) and ubuntu on my primary slave (hdb). I don't now if this is of importance...

---

### Post by merlinus on 2007-09-09
What is the mountpoint?

---

### Post by Ampi on 2007-09-09
/mnt/fedora

---

### Post by merlinus on 2007-09-09
Look in /media -- you might find the files, etc. there.

---

### Post by Ampi on 2007-09-09
nope :(
I only have my cdrom and ipod there....

---

### Post by merlinus on 2007-09-09
Post results of

```

sudo fdisk -l
cat /etc/fstab

```

---

### Post by Ampi on 2007-09-09
mmm, something changed since last time....

sudo fdisk -l

```

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          13      104391   83  Linux
/dev/hda2              14        4998    40042012+  8e  Linux LVM

Disk /dev/hdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4773    38339091   83  Linux
/dev/hdb2            4774        4866      747022+   5  Extended
/dev/hdb5            4774        4866      746991   82  Linux swap / Solaris
Note: sector size is 2048 (not 512)

Disk /dev/sda: 1015 MB, 1015021568 bytes
32 heads, 61 sectors/track, 253 cylinders
Units = cylinders of 1952 * 2048 = 3997696 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?      398636      983425  2283019262   72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(398635, 6, 23)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(983424, 30, 61)
Partition 1 does not end on cylinder boundary.
/dev/sda2   ?       86419     1078237  3872056480   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(86418, 26, 1)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(1078236, 17, 53)
Partition 2 does not end on cylinder boundary.
/dev/sda3   ?      957932     1949749  3872056384   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(957931, 2, 32)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(1949748, 25, 36)
Partition 3 does not end on cylinder boundary.
/dev/sda4   ?     1478321     1478349      110998    d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(1478320, 8, 25)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(1478348, 22, 13)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order


```

and fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=2596ce7d-0a93-4975-a56c-14b9bf57272e /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=3969b0e6-6281-4940-9964-7c28b8721607 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


```

---

### Post by merlinus on 2007-09-09
What is on sda?  Ubuntu fdisk command sure throws up lots of errors.

Which partition are you trying to mount?

---

### Post by Ampi on 2007-09-10
I want to mount hdb, I dont even know what sda is let alone what's on it...
But because my fdisk was clean before I mounten,  I tried it again this morning after restarting it and now it's clean again.

```

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          13      104391   83  Linux
/dev/hda2              14        4998    40042012+  8e  Linux LVM

Disk /dev/hdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4773    38339091   83  Linux
/dev/hdb2            4774        4866      747022+   5  Extended
/dev/hdb5            4774        4866      746991   82  Linux swap / Solaris


```

So before I try to mount again. Yesterday I tried 

```

sudo mount /dev/hdb1 /mnt/fedora

```
(If I try hdb or hdb2 it doesn't work.) 
Then I got only Grub and Lost&Found directories and my fdisk got so messed up. So something must be wrong with this mounting..

---

### Post by merlinus on 2007-09-10
sudo mount -t ext3 /dev/hdb1 /mnt/fedora

---

### Post by Ampi on 2007-09-10
Ow, sorry, my mistake!!
It's not hdb1 but hda1 I want to mount, now I would be mounting the disk I am on. 

But if I make the same command with hda1 I still only see Grub and Lost&Found, so now I am thinking that maybe the other documents are on another partition....:(..??

---

### Post by merlinus on 2007-09-10
You might be able to mount it from the live cd.

---

### Post by meierfra on 2007-09-10
Don't you want to mount hda2? hda1 only has about 100mb.

---

### Post by Ampi on 2007-09-11
the i guess it's hda2, but that still doesn't work. How can I use the cd to do it? What cd?

---

### Post by meierfra on 2007-09-11
What happens when you mount hda2  via "sudo mount  -t ext3 /dev/hda2 /mnt/fedora" ? Do you get an error message?

---

### Post by meierfra on 2007-09-11
> How can I use the cd to do it? What cd?

What did you use to install Ubuntu? The alternate cd or the live cd? If you have the life cd, you can boot it and  try to mount hda2 via

```
sudo mkdir /mnt/fedora
sudo mount -t ext3 /dev/hda2 /mnt/fedora

```

---

### Post by Ampi on 2007-09-12
mm.. I am not sure I understand. 

I have downloaded the .iso from the Ubuntu-site and installed it from there. But still, it must be possible to mount my other harddisk every time I boot my computer or just when I need it instead of needing a cd to do that?

More information:

```

user@pc:~$ sudo mount -t ext3 /dev/hda2 /mnt/fedora

mount: wrong fs type, bad option, bad superblock on /dev/hda2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

user@pc:~$ dmesg|tail
[   58.418233] NET: Registered protocol family 31
[   58.418245] Bluetooth: HCI device and connection manager initialized
[   58.418252] Bluetooth: HCI socket layer initialized
[   58.492820] Bluetooth: L2CAP ver 2.8
[   58.492829] Bluetooth: L2CAP socket layer initialized
[   58.559637] Bluetooth: RFCOMM socket layer initialized
[   58.560121] Bluetooth: RFCOMM TTY layer initialized
[   58.560127] Bluetooth: RFCOMM ver 1.8
[   72.125224] eth0: no IPv6 routers present
[ 2830.580997] VFS: Can't find ext3 filesystem on dev hda2.

```

---

### Post by meierfra on 2007-09-12
Maybe hda2 is not formated as an  ext3 file system. Post  the output of 

```
blkid
```

---

### Post by Ampi on 2007-09-12
ok, this is my blkid-output, it isnt suppose to give all my partitions?
```

/dev/dm-0: UUID="530835b5-6714-47f7-a9a7-ed7dc735d215" SEC_TYPE="ext2" TYPE="ext3"
/dev/dm-1: TYPE="swap" UUID="f22821a1-759f-4858-bde1-dd03f69177c7"
/dev/hda1: LABEL="/boot" UUID="852f7bd7-689b-4106-a583-7d66b3a66767" SEC_TYPE="ext2" TYPE="ext3"
/dev/hdb1: UUID="2596ce7d-0a93-4975-a56c-14b9bf57272e" SEC_TYPE="ext2" TYPE="ext3"
/dev/hdb5: UUID="3969b0e6-6281-4940-9964-7c28b8721607" TYPE="swap"

```

---

### Post by meierfra on 2007-09-12
> it isnt suppose to give all my partitions?

Yes it should.  That looks like something is wrong with  the "hda2" partition. Although that does not make much sense since your are able to boot into Fedora.  You might want to boot into Fedora and  run "bklid" in Fedora.

But I don't  really have any  idea what is going on,  and hopefully somebody else will be able to  give  you better advice.

---

### Post by meierfra on 2007-09-12
Maybe /dev/dm-0 is your Fedora partition? Try to mount it by its UUID:


```
sudo mount -t ext3  UUID="530835b5-6714-47f7-a9a7-ed7dc735d215"  /mnt/fedora
```

But this is just a wild guest. Anybody around here who has some experience with Fedora?

---

### Post by Ampi on 2007-09-13
I found the solution! 
Somebody (on the fedora-forum) told me that my documents are on my second partition. So that part was correct. The only problem is the file type system of that partition, which is Linux LVM. It seems to need some special treatment. This afternoon I will try to mount it and let you know... 
For anyone interested or with the same problem, this is the URL for mounting Linux LVM devices:
[http://www.linux-sxs.org/storage/fedora2ubuntu.html](http://www.linux-sxs.org/storage/fedora2ubuntu.html)

---

### Post by Ampi on 2007-12-16
I did never tell what happened!
I remember I tried my so found solution and it didn't work. So making sure my frustration didn't become boss over me :) I decided to let it go for a while. 
I was about to post again for some help, but I thought: let's try it again! AND IT WORKS!!! Maybe because now I'm using Gutsy Gibbon instead of Feisty Fawn or maybe I did something incorrect. Anyhow. 

The URL in the former post works perfectly well!!

---

### Post by Ampi on 2007-12-19
.

---

