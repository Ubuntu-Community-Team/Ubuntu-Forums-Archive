---
title: "Strange problem in accessing my hard disk"
date: 2006-11-17
forum: Hardware &amp; Laptops
---

### Post by ideasrex on 2006-11-17
I am experiencing a very strange situation since I bought a new Hard Disk  and after reinstalling both Windows and Kubuntu Edgy on it I cannot access my hard disk partitions. 
Earlier, with my old hard disk all the content was listed in /media folder.
And I was able to read my documents without any problem. However this time I wasn't that lucky, 
This is what i get in my /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=728826c7-1fe2-4538-8b70-55eceb3dda3e /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda6
UUID=28ba8bc1-3664-4f8c-afc7-706fc64c3f20 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0



here is what it says when i ran sudo fdisk -l 

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4272    34314808+   7  HPFS/NTFS
/dev/hda2            4273       23035   150713797+   f  W95 Ext'd (LBA)
/dev/hda3           23036       30401    59167395   83  Linux
/dev/hda5            4273       22752   148440568+   7  HPFS/NTFS
/dev/hda6           22753       23035     2273166   82  Linux swap / Solaris

I would appreciate very much if you could give me some suggestions on what to do with this.
I really like Kubuntu and I would like to use it much more in the future, but I need to fix this.

Thanks a lot in advance

---

### Post by K.Mandla on 2006-11-17
(Moved to the Hardware forum, where it should see more attention. ;) )

---

### Post by taurus on 2006-11-17
So you want to mount /dev/hda1, /dev/hda2, & /dev/hda5!!!  Here is something you can read.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by ideasrex on 2006-11-18
Thanks for the link :) it is great and helped me understand better my problem. However, it seems specific in my case since it didn't fix it. My /etc/fstab/ doesn't list my other partitions at all. :S There are only ext3 and swap partitions. 
Then I did mount -t auto /dev/hda1 and got the result of having my ntfs at least visible in /media but not accessible. 
When I try to open I don't have permissions then after running with root privileges I saw my documents but still couldn't copy any of them to my linux folder where I could work with it. 
This is all very confusing. If anyone had similar issue please help.

---

### Post by taurus on 2006-11-18
Okay, I guess I need to walk you thru it step by step then.  Open a terminal and edit your /etc/fstab.

```
sudo cp /etc/fstab  /etc/fstab.bak  <-- make a backup copy first...
gksudo gedit /etc/fstab
```
Now, add the following line to the end of it.

```

/dev/hda1   /media/Windows   ntfs   nls=utf8,umask=0222   0   0

```
Save it.  Then, create a mount point and mount it.

```
sudo mkdir /media/Windows
sudo mount -a
df -h  <-- you should see your /dev/hda1 mounted on /media/Windows...
```

---

