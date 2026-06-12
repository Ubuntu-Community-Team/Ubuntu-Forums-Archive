---
title: "My IDE doesn't show up"
date: 2006-12-14
forum: Hardware &amp; Laptops
---

### Post by deodeep on 2006-12-14
Hello,

I have a 160 GB SATA HDD, with the following partitions...

C - Windows/NTFS
D - NTFS
E - NTFS
F - NTFS
G - DVD-RW
L - Linux - Ext3
S - Sawp

I have installed Ubuntu 6.10 on the last two partition of the Sata.
Everyting is working fine.

Now, I also have a 40 GB IDE. I formatted it as 2 partitions of 20 Gb each on FAT32 ( Just so that I could share a partition both on Windows and Ubuntu )

Now, how do I make this HDD show up in Ubuntu ?

The 4 NTFS drives along with my FDD and DVD are seen and accessible. But there is no sign of the IDE in Ubuntu. Although I can access them thhrough windows.

Help would be appreciated.

Thanks :)

---

### Post by bernied on 2006-12-14
Try (in a terminal):
```
sudo fdisk -l
```
Is the drive in the list? Write down the two names of the partitions, something like - /dev/-d--
If yes, then create a couple of mount points:
```
sudo mkdir /media/{fat1,fat2}
```
You should change the names to something more meaningful. The other place you might put the mountpoints is in /mnt/

Then see if they mount ok:
```
sudo mount -t vfat /dev/xdyz /media/fat1
```
Instead of xdyz, you will need the name of the partition, as shown from that fdisk command above.
If they mount ok then create an entry in /etc/fstab.
```
sudo nano /etc/fstab
```

Read the output from:
```
man mount
```to work out how to create this entry. Or come back here and ask.

---

### Post by deodeep on 2006-12-14
Thanks for Replying :).... Here's what I did.

First, I executed...

```
sudo fdisk -l
```

The output turned out to be 

```


Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2550    20482843+   c  W95 FAT32 (LBA)
/dev/hda2            2551        4865    18595237+   f  W95 Ext'd (LBA)
/dev/hda5            2551        4865    18595206    b  W95 FAT32

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3570    28675993+   7  HPFS/NTFS
/dev/sda2            3571       19425   127355287+   f  W95 Ext'd (LBA)
/dev/sda5            3571        7140    28675993+   7  HPFS/NTFS
/dev/sda6            7141       11984    38909398+   7  HPFS/NTFS
/dev/sda7           11985       17206    41945683+   7  HPFS/NTFS
/dev/sda8           17207       19164    15727603+  83  Linux
/dev/sda9           19165       19425     2096451   82  Linux swap / Solaris

```



From the above, I make out that the 2 IDE partitions are 

```

/dev/hda1
/dev/hda5

```


Now, I created 2 mount points

```

sudo mkdir /media/pata1
sudo mkdir /media/pata2

```

Then. I

```

sudo mount -t vfat /dev/hda1 /media/pata1

```

After this, I

```
sudo nano /etc/fstab
```

Here, I added,

```

/dev/hda1       /media/pata1     vfat    iocharset=utf8,umask=000        0       0

```

Thus, the overall /etc/fstab looked like
```


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=7f28ab95-fdb7-42ea-822c-a27e5857ef3f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=36E8642FE863EB95 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=5208A5F908A5DBEB /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=82A8A1E6A8A1D945 /media/sda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=0278689D78689169 /media/sda7     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda9
UUID=eb4ac50d-f253-4b35-becc-9e04106c1ce9 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/pata1     vfat    iocharset=utf8,umask=000        0       0

```


Thus, atleast I should get the first FAT32 partition right ??

Nope, I don't :(

Where Did I go wrong ?

---

### Post by taurus on 2006-12-14
You only added /dev/hda1 in /etc/fstab!!!  Therefore, you need to add another entry for /dev/hda5...

```

/dev/hda5       /media/pata2     vfat    iocharset=utf8,umask=000        0       0

```

---

### Post by deodeep on 2006-12-14
Did that too,

now my /atc/fstab looks like 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=7f28ab95-fdb7-42ea-822c-a27e5857ef3f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=36E8642FE863EB95 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=5208A5F908A5DBEB /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=82A8A1E6A8A1D945 /media/sda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=0278689D78689169 /media/sda7     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda9
UUID=eb4ac50d-f253-4b35-becc-9e04106c1ce9 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/pata1     vfat    iocharset=utf8,umask=000        0       0
/dev/hda5       /media/pata2     vfat    iocharset=utf8,umask=000        0       0

```

Still, I don't see the drives !!

---

### Post by taurus on 2006-12-14
Now, you have to mount them!!!

```
sudo mount -a
df -h
```

---

### Post by deodeep on 2006-12-14
Ok :)

Thanks. Now the drives are accessible by going to the /media folder through the file explorer.

But how do I add the drives to the "Places" menu ?

Also, on the Desktop ?

Thanks for your time and Help !

---

### Post by taurus on 2006-12-14
There should be icons on your Desktop for those drives!!!  Everything mounts on /media will have an icon on the Desktop...

---

### Post by deodeep on 2006-12-14
Really ?

There isn't !! 

Just 4 icons of the SATA HDD and a folder I created. That's all ! 

Is a restart needed ?

---

### Post by taurus on 2006-12-14
Sure, reboot doesn't hurt.

---

### Post by deodeep on 2006-12-14
You know what ?

You were right :p, A reboot doesn't hurt at all. Plus, it did the trick :) Yayyy ! 

Thanks a lot you guys. Someone told me the folks at Ubuntuforums are really helpful and I could find all the help I want. Now I know he was so truly right..

Thanks again!!

---

### Post by taurus on 2006-12-14
Glad to hear everything is working now, with like 6 icons on your Desktop for your drives!!!  ;)

---

