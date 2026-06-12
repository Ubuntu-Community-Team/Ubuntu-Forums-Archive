---
title: "how tochange read only disk"
date: 2007-07-05
forum: Hardware &amp; Laptops
---

### Post by canale on 2007-07-05
Hello all,
congratulations to the editors of this forum. Very useful.

I have a problem in change the permissions on 2 partitions of a disk.  Ubuntu says it is read only, therefore I can open and copy files but not edit them. Any help would be very much appreciated.

Thanks

---

### Post by kevinlyfellow on 2007-07-05
Just a bit of lingo for you, the editors are called moderators here (who do a fabulous job) and there is plenty of credit that goes to all who contribute to the forum, with both questions and answers.

What I think you need to do is to edit your 'fstab' file (filesystem tab, it keeps track of the filesystems and their properties on you computer).  Post the file here 
```
gedit /etc/fstab
```

Here is a link that you may find useful [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by canale on 2007-07-05
Many thanks for your reply. This is my fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=dfa46f6b-e699-4e3c-bfea-8c3980db059e /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=f5c0c5a6-cc9e-483a-be55-9dddff7a00f1 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by kevinlyfellow on 2007-07-05
Your welcome

I only see one partition on you computer that's currently setup.  I can tell you what lines to insert if you can either 1) give me the device names of the partitions you want to setup 2) post the output of the following:
```
sudo fdisk /dev/hda
```
then enter p (prints the partition table) and then q (quits out of the program).

---

### Post by canale on 2007-07-05
this is the output of the command

> root@ubuntu01:~# sudo fdisk /dev/hda

The number of cylinders for this disk is set to 4865.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)


the name of the 2 partitions I want to change permissions of are:>  SICUREZZA 80 G and > TUTTO 40 G

---

### Post by kevinlyfellow on 2007-07-05
:-)  Let's try that one again.  

After ```
sudo fdisk /dev/hda
``` **then enter p and then quit the program by entering q**.  This will print the partition table so that I better understand how your partitions are setup and I will know all the names I need to (the names I'm referring to are things like /dev/hda2 and /dev/hda3).

Edit: are the seperate harddisks or seperate partitions?

Edit again:  Here's another way of doing it.  Give me the output of the command
```
sudo fdisk -l /dev/hda
```

---

### Post by canale on 2007-07-05
this is the result of the first command
> Command (m for help): sudo fdisk /dev/hda
Building a new sun disklabel. Changes will remain in memory only,
until you decide to write them. After that, of course, the previous
content won't be recoverable.

Drive type
   ?   auto configure
   0   custom (with hardware detected defaults)
   a   Quantum ProDrive 80S
   b   Quantum ProDrive 105S
   c   CDC Wren IV 94171-344
   d   IBM DPES-31080
   e   IBM DORS-32160
   f   IBM DNES-318350
   g   SEAGATE ST34371
   h   SUN0104
   i   SUN0207
   j   SUN0327
   k   SUN0340
   l   SUN0424
   m   SUN0535
   n   SUN0669
   o   SUN1.0G
   p   SUN1.05
   q   SUN1.3G
   r   SUN2.1G
   s   IOMEGA Jaz
Select type (? for auto, 0 for custom): p
You may change all the disk params from the x menu

Command (m for help): 


---

### Post by canale on 2007-07-05
Hi again
this is what I get after the last command

> root@ubuntu01:~# sudo fdisk -l /dev/hda

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4678    37576003+  83  Linux
/dev/hda2            4679        4865     1502077+   5  Extended
/dev/hda5            4679        4865     1502046   82  Linux swap / Solaris
root@ubuntu01:~# 


please help me

---

### Post by kevinlyfellow on 2007-07-05
That's what I needed.  So add the line

```
sudo mkdir /media/hda2
gksudo gedit /etc/fstab
```

and add the following line to the file
```

/dev/hda2 /media/hda2 vfat rw,auto,users,gid=users,umask=0007 0 0 

```

---

