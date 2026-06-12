---
title: "trying to mount hdd but its always busy"
date: 2006-02-07
forum: Hardware &amp; Laptops
---

### Post by maxxag on 2006-02-07
I keep trying to mount my /dev/sdb, a fat32 formated hdd that will act as an intermediary between windows and linux, but every time i try and mount it it either says the mount directory is busy or the drive itself is busy or already mounted.  how can i mount it to the desktop reliably, ive used all the help in the  threads too no avail!

thanks!

---

### Post by Sutekh on 2006-02-07
This is the new system now?  Without the RAID setup?

If you want to mount it permanently rather than having to issue a mount command everytime, then could you post the output of 
```
sudo fdisk -l
```So I can see where the partition issss (it's probably /dev/sdb1, but just to be sure), and
```
cat /etc/fstab
```So I can see your mounting options.



The following is just a guess, without seeing the information.

You will need similar lines to these to mount FAT32 partitions.
```

sudo mkdir /media/fat32_mount
```To make the folder to mount the FAT32 partition to.

And add this line to your /etc/fstab to mount the FAT32 partition.
```

/dev/sdb1 /media/fat32_mount vfat iocharset=utf8,umask=000 0 0

```

But give us the output of fdisk and fstab first.

---

### Post by maxxag on 2006-02-07
ya, i ditched raid and put windows on the 80gig IDE disk since it wont recognise SATA drives anymore (and i cant find the damn drivers to get it too! :-( ) and linux on one of the SATA disks, and finally got a proper grub dual boot setup (which is freakin cool).    

first heres the info you need:

max@max:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14215   114181956   83  Linux
/dev/sda2           14216       14593     3036285    5  Extended
/dev/sda5           14216       14593     3036253+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241   83  Linux
max@max:~$

________________________

max@max:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

max@max:~$

i get to the point your talking about and it does like so:

max@max:~$ sudo mount /dev/sdb /media/windows/ -t vfat -o iocharset=utf8,umask=000
mount: /dev/sdb already mounted or /media/windows/ busy
max@max:~$

---

### Post by Sutekh on 2006-02-07
[QUOTE=maxxag]
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241   83  Linux
max@max:~$
[/QUOTE]
Um, sdb1 is not a FAT32 partition, its an ext3 one by the look of it.

A FAT32 entry from fdisk would look like
```
 Device Boot Start End Blocks Id System
/dev/hdb1 * 1 9729 78148161 c W95 FAT32 (LBA)
```

How did you create the partition on sdb1?  The Ubuntu installer?  GParted?  Something else?

---

### Post by maxxag on 2006-02-07
hrm, ive formatted it with the disk utility in ubuntu as fat32, should i try and format it with fdisk striaght from the command line?

---

### Post by Sutekh on 2006-02-07
[QUOTE=maxxag]hrm, ive formatted it with the disk utility in ubuntu as fat32[/CODE]I did the same when I installed Ubuntu, I don't know why it didn't work for you.

I'm not up to speed on using fdisk to partition.  You can install GParted from the repositories that is a nice GUI to format partitions.

```
sudo apt-get install gparted
```

---

### Post by maxxag on 2006-02-07
in gpartd (which i had and used, and forgot about) it has the sdb as fat32

---

### Post by Sutekh on 2006-02-07
??

oh well we can try and see what happens

(You left out the '1' in sdb1 last time)
```
sudo mount /dev/sdb1 /media/windows/ -t vfat -o iocharset=utf8,umask=000 0 0
```

---

### Post by maxxag on 2006-02-07
wow, sutekh, you sir are a ubuntu god!  thanks!  now what do i put into the fstab to make this a permanent arangement?

---

### Post by Sutekh on 2006-02-07
Haha, Sutekh (Set) was an Egyptian god, not African! :mrgreen: 


Anyway... you need to edit your fstab, but first we'll back it up.
```
sudo cp /etc/fstab /etc/fstab_20060802
```(I like using date backups)

Then we will edit it
```
sudo gedit /etc/fstab
```
Then we will slot in the line to make it permanent
```

/dev/sdb1 /media/windows/ -t vfat-o iocharset=utf8,umask=000 0 0
```
After you save you don't need to reboot, just issue
```
sudo mount -a
```
and you should be kicking!

---

### Post by maxxag on 2006-02-08
uh oh, i got this error:

max@max:~$ sudo mount -a
[mntent]: line 9 in /etc/fstab is bad
max@max:~$

edit: heres my fstab again, this time with what you added, is the syntax wrong or somthing?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb1 /media/windows/ -t vfat-o iocharset=utf8,umask=000 0 0

---

### Post by Sutekh on 2006-02-08
[QUOTE=maxxag]
/dev/sdb1 /media/windows/ -t vfat-o iocharset=utf8,umask=000 0 0[/QUOTE]
Try
```
/dev/sdb1 /media/windows/ vfat iocharset=utf8,umask=000 0 0
```

---

### Post by Sutekh on 2006-02-08
[QUOTE=maxxag]
/dev/sdb1 /media/windows/ -t [COLOR="DarkRed"]vfat-o[/COLOR] iocharset=utf8,umask=000 0 0[/QUOTE]
Either I think would work the culprit is in red - no space between **vfat** and the **-o**

That's my fault, I have a dodgy KVM switch that screws up my typing sometimes, and getting the typing correct in CODE tags is very important.

---

### Post by maxxag on 2006-02-08
hrm, i got the same error again

after i edited the fstab for that space that is

---

### Post by Sutekh on 2006-02-08
Did you try the one with out the **-t** and the **-o**?

---

### Post by maxxag on 2006-02-08
cool! seems to have worked, no error output anyway, thanks sutekh! i owe you one :-)

---

### Post by Sutekh on 2006-02-08
[QUOTE=maxxag]cool! seems to have worked, no error output anyway, thanks sutekh! i owe you one :-)[/QUOTE]
Sorry for the mix up.  I still don't know why the manual **mount** command works with the **-t** (filesystem type flag) and **-o** (options flag), but the entry in /etc/fstab doesn't like them.

No errors is good!

---

### Post by maxxag on 2006-02-08
pretty soon i hope i can help people and not just mooch help, thanks again man!

---

### Post by Sutekh on 2006-02-08
Well keep at it, you'll pick it real quick!

---

