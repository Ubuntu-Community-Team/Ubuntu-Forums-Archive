---
title: "[SOLVED] Root at 100%  out of space"
date: 2008-08-17
forum: General Help
---

### Post by flintflake on 2008-08-17
I have a 16GB partition as my Ubuntu drive.   Like 2 days ago, I had 6GB left.   Over the last 2 days, I have used 6GB and now I have no room!!

I've only used Firefox, Banshee (to stream from my NAS), and that's about it.

I have done all of the synaptic cleanups and auto clean auto remove and i'm still at 99%.  I have deleted all of the log files as well.

What else can i run to reclaim some of my space back!!

---

### Post by flintflake on 2008-08-17
here's the output of my utilization:

Filesystem            Size  Used Avail Use% Mounted on
varrun                633M  212K  633M   1% /var/run
varlock               633M     0  633M   0% /var/lock
udev                  633M   72K  633M   1% /dev
devshm                633M     0  633M   0% /dev/shm
lrm                   633M   34M  599M   6% /lib/modules/2.6.22-15-generic/volatile
/dev/hdd1              59G   56G  2.9G  96% /media/hdd1
/dev/hdd2              54G   29G   25G  54% /media/hdd2
overflow              1.0M   24K 1000K   3% /tmp

Now... conky shows my root to be hda5.     Why isn't hda5 showing up when i do df -h  ????

Here's my fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6
#UUID=f3a3ce58-80e1-477b-aa85-b00fa0880bd9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=AAF07DB2F07D857B /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda5
UUID=f3a3ce58-80e1-477b-aa85-b00fa0880bd9 /media/hda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda7
#UUID=dcfe2994-63b6-4c64-bd29-09427d15dc26 /media/hda7     ext3    defaults        0       2
# /dev/hdd1
UUID=BA4C6C644C6C1CFF /media/hdd1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hdd2
UUID=2C18885318881E48 /media/hdd2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda6
UUID=d6558dc0-1963-461c-9cb0-eb18e31a12c4 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

And Fdisk:

Disk /dev/hda: 30.6 GB, 30606151680 bytes
255 heads, 63 sectors/track, 3720 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9044fb22

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/hda2            1276        3720    19639462+   f  W95 Ext'd (LBA)
/dev/hda5            1276        3465    17591143+  83  Linux
/dev/hda6            3466        3720     2048256   82  Linux swap / Solaris

Disk /dev/hdd: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb80926dd

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        7649    61440561    7  HPFS/NTFS
/dev/hdd2            7650       14593    55777680    7  HPFS/NTFS


HELP!!!

---

### Post by mikewhatever on 2008-08-17
The output of df -h please.

Edit: I am confused. According to fstab hda6 is both your root and swap, while according to fdisk, root is hda5 and swap hsa6.
Have someone been tinkering with fstab?

---

### Post by flintflake on 2008-08-17
that would be me.   I resized a partition and got tons of grub errors, but that was months ago.   Everything has been "ok" since.  

How do I fix fstab?  Is that's what's causing my issues?

this is the output you requested:

Filesystem Size Used Avail Use% Mounted on
varrun 633M 212K 633M 1% /var/run
varlock 633M 0 633M 0% /var/lock
udev 633M 72K 633M 1% /dev
devshm 633M 0 633M 0% /dev/shm
lrm 633M 34M 599M 6% /lib/modules/2.6.22-15-generic/volatile
/dev/hdd1 59G 56G 2.9G 96% /media/hdd1
/dev/hdd2 54G 29G 25G 54% /media/hdd2
overflow 1.0M 24K 1000K 3% /tmp

---

### Post by sisco311 on 2008-08-17
post:
```
sudo blkid
```

---

### Post by flintflake on 2008-08-17
here it is:

/dev/hda1: UUID="AAF07DB2F07D857B" TYPE="ntfs" 
/dev/hda5: UUID="f3a3ce58-80e1-477b-aa85-b00fa0880bd9" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda6: TYPE="swap" UUID="d6558dc0-1963-461c-9cb0-eb18e31a12c4" 
/dev/hdd1: UUID="BA4C6C644C6C1CFF" LABEL="New Volume" TYPE="ntfs" 
/dev/hdd2: UUID="2C18885318881E48" LABEL="New Volume" TYPE="ntfs"

---

### Post by sisco311 on 2008-08-17
edit the fstab to:
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda5
UUID=f3a3ce58-80e1-477b-aa85-b00fa0880bd9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=AAF07DB2F07D857B /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hdd1
UUID=BA4C6C644C6C1CFF /media/hdd1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hdd2
UUID=2C18885318881E48 /media/hdd2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda6
UUID=d6558dc0-1963-461c-9cb0-eb18e31a12c4 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
and reboot.

---

### Post by flintflake on 2008-08-17
pasted your fstab, rebooted, and it still shows almost full.  Conky reports only 184MB left.

What else can i do?

---

### Post by drs305 on 2008-08-17
> **flintflake said:**
> What else can i do?

Run the following command to find any Trash folders:
```
sudo find / -type d -iname *Trash* | grep Trash
```

Once you have located them, open nautilus with administrative power and navigate to and delete any 'Trash' folders.

---

### Post by az on 2008-08-17
You resized a partition, but did you resize the filesystem on it?

---

### Post by flintflake on 2008-08-17
> **drs305 said:**
> Run the following command to find any Trash folders:
```
sudo find / -type d -iname *Trash* | grep Trash
```

Once you have located them, open nautilus with administrative power and navigate to and delete any 'Trash' folders.

That done it!   I had 11 GB in the root .trash folder.   

Marking as Solved!   Thanks everyone for their fast responses!

---

### Post by Loaded.len on 2008-08-17
A few weeks ago, I was using dd_rescue to recover a bunch of files from a dead drive..then used testdisk and photorec to read through the image I made. This worked like a charm, except that when I tried to remove working directories that photorec made I didn't have permissions.  No problem, I opened up Nautilus as root and blew them all away.  Then a couple days later I noticed I was out of HDD space, and couldn't account for it.

```
find ./ -type f -size +1G
```

That searched for all the files on my drive over 1GB...most of which lived in .local/share/Trash.  Seems that if you delete files in Nautilus as root, then they're stuck there.  If memory serves, I had to do sudo su to finally rid myself of all those files.

---

