---
title: "How to straighten out Grub/partitions"
date: 2009-06-24
forum: Installation &amp; Upgrades
---

### Post by Bobrm2 on 2009-06-24
This began while upgrading from 8.04 to 9.0x. I've Ubuntu on three partitions.
   1st. A failed upgrade with all old files backed up. The attempted upgrade was 8.04 to current version. sda08, Not usuable with out a lot of patience, reconfiguring the wireless settings etc.

   After creating an ISO I've a good 9.04 and currently using it on it's seperate partition. sda01 Wireless up and running etc.

   Finally another 9.04 version on it's partition, but I do not know which one partition.

   I know that the /boot is on sda01. An post the following in hopes that someone can explain it to me(?). Also what other commands can I run inorder to begin to straighter this out. I would think that reconfiguring the Partitions may be the place to begin? Old saying "When your in the hole, stop digging' applies here. Thank you.

Bob

---

### Post by carml on 2009-06-24
Yes,the first thing to do is to know what is the complete list of partition and their use.If I'm not wrong a useful command to use in the terminal is ```
df
```, otherwise you can make use of Gparted if installed by Sistem->Administration->Partitions Editor.
An other thing to know is what you mean to do with 8.04and 9.04,you wish both of them installed? 
I hope this could help you. :)

---

### Post by carml on 2009-06-24
An other useful sommand via terminal is ```
sudo fdisk -lu
```.
Here is mine for example: first is df```
carmelo@ubuntu:~$ df
File system         blocchi di 1K    Usati   Dispon. Uso% Montato su
/dev/sda5             11897832  10111544   1426516  88% /
varrun                 1037132       116   1037016   1% /var/run
varlock                1037132         0   1037132   0% /var/lock
udev                   1037132        60   1037072   1% /dev
devshm                 1037132        44   1037088   1% /dev/shm
lrm                    1037132     40000    997132   4% /lib/modules/2.6.24-24-generic/volatile
gvfs-fuse-daemon      11897832  10111544   1426516  88% /home/carmelo/.gvfs
/dev/sda2             72380852  65196568   7184284  91% /media/disk
/dev/sda3             64131476  63192372    939104  99% /media/disk-1

```
and second fdisk -lu
```
carmelo@ubuntu:~$ sudo fdisk -lu
[sudo] password for carmelo: 

Disco /dev/sda: 160.0 GB, 160041885696 byte
255 heads, 63 sectors/track, 19457 cylinders, totale 312581808 settori
Units = settori of 1 * 512 = 512 bytes
Disk identifier: 0x6d79525e

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1              63    14667344     7333641   27  Sconosciuto
/dev/sda2   *    14667345   159429059    72380857+   7  HPFS/NTFS
/dev/sda3       159429060   287692019    64131480    7  HPFS/NTFS
/dev/sda4       287692020   312576704    12442342+   5  Esteso
/dev/sda5       287692083   311677064    11992491   83  Linux
/dev/sda6       311677128   312576704      449788+  82  Linux swap / Solaris

```

---

### Post by raymondh on 2009-06-24
Hello Bob,

Valuable to me is having a visual aid.  I usually print out a gparted screenshot of what my disc looks like.... plus, it also has the descriptions and hierarchy on the box below.

That and  'fdisk -l' are what I go by.

Another tool of value is meierfra's bootinfoscript for boot related problems that may arise after re-working my disk/s. 

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

In case you decide to use this .... you need to download the file and save.  After downloading, open a terminal to type

```
sudo bash ~/Desktop/boot_info_script*.sh
```

which creates (and saves to desktop) a RESULTS.TXT file.

Good luck .... post back should you require assistance or a second opinion on your partitioning re-work.  Back up your files first.

Happy Ubuntu-ing.

---

### Post by Bobrm2 on 2009-06-24
Carml,
   I intended to go back to 8.04 and use it as learning tool, because of the shape it's in, I felt that I would be more knowledgeable. 

Thank you for the commands that generated the following;
bob@bob-desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1              8752336   3678240   4629500  45% /
tmpfs                   222192         0    222192   0% /lib/init/rw
varrun                  222192       108    222084   1% /var/run
varlock                 222192         0    222192   0% /var/lock
udev                    222192       160    222032   1% /dev
tmpfs                   222192        88    222104   1% /dev/shm
lrm                     222192      2392    219800   2% /lib/modules/2.6.28-11-generic/volatile
bob@bob-desktop:~$ sudo fdisk -lu
[sudo] password for bob: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xedb1edb1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    17783954     8891946   83  Linux
/dev/sda2        27181980   234436544   103627282+   5  Extended
/dev/sda5       111314385   111716009      200812+  83  Linux
/dev/sda6       111716073   208909259    48596593+  83  Linux
/dev/sda7       208909323   218275154     4682916   82  Linux swap / Solaris
/dev/sda8        27182106   111314384    42066139+  83  Linux
/dev/sda9       218275218   223223174     2473978+  83  Linux
/dev/sda10      233633358   234436544      401593+  82  Linux swap / Solaris

Partition table entries are not in disk order
bob@bob-desktop:~$ 

This shows the problems, 8.04 is located on /dev/sda 8/linux.

The 9.0x I wish to keep is /dev/sad1/.

I don't know where the other 9.0x is located? Size of the file should give me a clue. 

Your comments most appreciated

---

### Post by carml on 2009-06-24
I thought of a way to know it: we can just see the kernel numbers,if you didn't install manually modified kernels.
Can you please post here the content of the file menu.lst? It's under /boot/grub, you need to access it via terminal by ```
sudo gedit /boot/grub/menu.lst

```.
Doing so we'll know which partition is associated with 9.04 and so on.

---

### Post by Bobrm2 on 2009-06-24
Carmel, here is the menu.lst file. Also have done as Raymond suggested. Tools are gathered; but I have to take the wife to the Doc, be late this evening before I can return to the forum.

Thanks, everyone. I will get back ASAP

Bob

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		56d8b3f2-4f3a-49d1-b2e3-1ce717396eda
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=56d8b3f2-4f3a-49d1-b2e3-1ce717396eda ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		56d8b3f2-4f3a-49d1-b2e3-1ce717396eda
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=56d8b3f2-4f3a-49d1-b2e3-1ce717396eda ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		56d8b3f2-4f3a-49d1-b2e3-1ce717396eda
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=56d8b3f2-4f3a-49d1-b2e3-1ce717396eda ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		56d8b3f2-4f3a-49d1-b2e3-1ce717396eda
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=56d8b3f2-4f3a-49d1-b2e3-1ce717396eda ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		56d8b3f2-4f3a-49d1-b2e3-1ce717396eda
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		Ubuntu 8.10, kernel 2.6.27-14-generic (on /dev/sda8)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=a9ecb9b4-96ff-4ff7-ba77-3775a72ae99b ro vga=normal 
initrd		/boot/initrd.img-2.6.27-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode) (on /dev/sda8)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=a9ecb9b4-96ff-4ff7-ba77-3775a72ae99b ro single 
initrd		/boot/initrd.img-2.6.27-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		Ubuntu 8.10, kernel 2.6.27-13-generic (on /dev/sda8)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.27-13-generic root=UUID=a9ecb9b4-96ff-4ff7-ba77-3775a72ae99b ro vga=normal 
initrd		/boot/initrd.img-2.6.27-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		Ubuntu 8.10, kernel 2.6.27-13-generic (recovery mode) (on /dev/sda8)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.27-13-generic root=UUID=a9ecb9b4-96ff-4ff7-ba77-3775a72ae99b ro single 
initrd		/boot/initrd.img-2.6.27-13-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		Ubuntu 8.10, kernel 2.6.27-12-generic (on /dev/sda8)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.27-12-generic root=UUID=a9ecb9b4-96ff-4ff7-ba77-3775a72ae99b ro vga=normal 
initrd		/boot/initrd.img-2.6.27-12-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		Ubuntu 8.10, kernel 2.6.27-12-generic (recovery mode) (on /dev/sda8)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.27-12-generic root=UUID=a9ecb9b4-96ff-4ff7-ba77-3775a72ae99b ro single 
initrd		/boot/initrd.img-2.6.27-12-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		Ubuntu 8.10, memtest86+ (on /dev/sda8)
root		(hd0,7)
kernel		/boot/memtest86+.bin  
savedefault
boot

---

### Post by Bobrm2 on 2009-06-30
I've finally got back to me desk. Hope there is still and interest. I'm curious about the comment "Partition table entries are not in disk order"? What does it mean, and how can I change it. Suspect it has  to do with "Grub"??

Thank you

Bob

---

### Post by Bobrm2 on 2009-06-30
Should have "Googled". This answered the question about how to realign the partition table.
[http://www.mail-archive.com/grub-devel@gnu.org/msg02449.html](http://www.mail-archive.com/grub-devel@gnu.org/msg02449.html)

---

