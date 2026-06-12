---
title: "Hard Disk Showing Incorrect Free Space"
date: 2005-12-14
forum: Hardware &amp; Laptops
---

### Post by walnut on 2005-12-14
Hi,

I've a 200gb sata drive connected to my computer that should be almost full but when I check the available space with df or KDiskFree it tells me that it's only 2% full with 180 gb free. I know this is not accurate as one folder alone has over 100gb.

Here's a copy of my fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc4       /home           ext3    defaults        0       2
/dev/hdc1       /media/hdc1     vfat    user,rw,auto,umask=000        0       0
/dev/hdd1       /media/hdd1     vfat    user,rw,auto,umask=000       0       0
/dev/sda1       /media/sda1     vfat    user,rw,auto,umask=000       0       0
/dev/hdc5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


```

Can anyone tell me what's wrong? I'm afraid to use the drive as it is in case some other data gets corrupted.:(

---

### Post by psusi on 2005-12-14
Which partition is the one you think has the wrong free space?  I assume that this 100 gb folder you mentioned is on the 'broken' partition?

Could you explain a bit more about your configuration.  From the looks of your fstab you have two hard disks each with a few partitions.  How big are they and what are they used for?

The output of fdisk -l would be helpful, as well as df.  

If you are sure that the reported sizes are wrong, then the filesystem may be damaged and you will want to unmount it and fsck it.

---

### Post by walnut on 2005-12-14
Sorry. Should have thought of that. Hard drive I'm havin the trouble with is /dev/sda1.

I do have two hard drives in the computer. A 20gb IDE "Operating Systems" drive and a 200gb SATA storage drive. Use Windows too so that's why the storage drive is FAT32 (although I'm now considering leaving Windows all together:) ).

Ubuntu did give me an error about an incorrectly formated partition when I was installing it but I ignored the error as I wasn't sure how much I'd use Ubuntu and didn't wanna risk loosing data. If I was to run fsck on it, is there any risk of loosing my data?

P.S. Absolutely love Ubuntu. Haven't used Windows since I installed it

---

### Post by psusi on 2005-12-14
Ok, but what does df and fdisk -l have to say about /dev/sda1?

And no, you won't loose any data that isn't already lost by fscking it.

---

### Post by walnut on 2005-12-14
df:
```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hdc2              5961312   3043728   2614760  54% /
tmpfs                   518324         0    518324   0% /dev/shm
tmpfs                   518324     12588    505736   3% /lib/modules/2.6.12-10-3 86/volatile
/dev/hdc4              3162452   2440256    561548  82% /home
/dev/hdc1              9757936         8   9757928   1% /media/hdc1
/dev/sda1            195310688   5540960 189769728   3% /media/sda1

```

fdisk -l:
```

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24321   195358401    c  W95 FAT32 (LBA)

```

---

### Post by psusi on 2005-12-14
What does du -sh /media/sda1 show?

I'd say go ahead and umount /media/sda1 and fsck /media/sda1.

---

### Post by walnut on 2005-12-14
du says 185gb used. Sounds about right.

I'll run fsck on it so. Anything I should know before I do (don't worry, I am planning on reading the man page)?

---

### Post by psusi on 2005-12-14
Not that I can think of... should be as simple as running fsck on it after unmounting.  Let it fix it if it asks and all shoul be right with the world.

---

### Post by walnut on 2005-12-14
fsck seems to only be for ext2 filesystems. I've got FAT32

Edit:
Never mind. Found dosfsck. Trying it now

---

### Post by walnut on 2005-12-14
Just one last post to say that it worked. Many thanks for all your help psusi.

For anyone else that might need this here's what I ran: 
```
 sudo dosfsck -vr /dev/sda1 
```
(partition was unmounted)

---

### Post by psusi on 2005-12-14
If you run fsck /media/sda1 then fsck will notice that fstab says it is fat, and run dosfsck instead. Otherwise you can use the -t option to specify the filesystem type just like with mount.

---

### Post by gabriello on 2007-10-12
....Wow!
I had the same problem and it worked for me too!
Now I can enjoy >5Gb of free space on my portable hard disk!
Thank you!

G.

---

