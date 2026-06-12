---
title: "[SOLVED] Problems Merging Partitions"
date: 2008-07-09
forum: Hardware
---

### Post by Moey on 2008-07-09
Hello All,

I have a 160gb hard drive in my linux media server.  I currently have 3 partitions.

First partition is sda1 and it is 60gb.  Just did a fresh install of hardy on it.

Second partition is sda2 and it is 89gb.  It is ext2 and I had all my media saved to it that I transfered to the first partition (sda1)

Third partition is sda3 and it is 1gb. This is swap space.

Now that I have all my media put onto the ubuntu partition (sda1) I would like to delete sda2 and expand sda1 to use the rest of the space of the disk.

To do this I boot off the live cd, but after I delete sda2, I cannot resize sda1 to use the rest of the disk.

I would just backup all of my media onto an external hard drive, then do a fresh install on 1 partition, and transfer media back, but I don't have access to an external disk at this time.

any help would be greatly appricated

---

### Post by logos34 on 2008-07-09
Try the [Gparted live cd.  ]("http://gparted.sourceforge.net/livecd.php")

---

### Post by Moey on 2008-07-09
> **logos34 said:**
> Try the [Gparted live cd.  ]("http://gparted.sourceforge.net/livecd.php")

Is this any different than the Ubuntu live cd that has Gparted on it that I am currently using?

---

### Post by logos34 on 2008-07-09
It's got a newer version, not much different, though.  But using the Gparted live cd sometimes works where gparted on the ubuntu cd fails.  

based on the info provided, I can't think of any reason why it won;t let you expand sda1 to take up the unallocated space.

---

### Post by Moey on 2008-07-09
Im just download and booted from the Gparted live cd, and I am getting the same problem...

I have 89 gigs unallocated, but cant extend my main partition

wtf.....

really frustrating, have been setting this up for a while now and every step is a new problem

thanks for the idea though!

---

### Post by logos34 on 2008-07-09
yes, odd...

what does 
[B]
sudo fdisk -l[/B]

show?

Maybe try running 

sudo fsck /dev/sda1

The only other thing that comes to mind is maybe there's some error in the partition table.  Use TestDisk to find out.  (yu can run it from ubuntu on the hard disk).

sudo apt-get install testdisk

sudo testdisk

---

### Post by Moey on 2008-07-09
Alright

After doing fdisk -l, I get

```
moey@moey-server:~$ sudo fdisk -l
[sudo] password for moey: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa70da70d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7746    62219713+  83  Linux
/dev/sda3            7747        7779      265072+  82  Linux swap / Solaris
```

And for the FSCK,  it says that running that onto a mounted filesystem may cause severe file system damage.

I assume I am should run that off the live cd.

I'll give test disk a shot.

Also thanks again for the extended help logos34, people like you are the reason I love ubuntu

---

### Post by Moey on 2008-07-09
I have TestDisk up and running, but not quite sure what I should be doing with it.  It does see all 3 partitions...

---

### Post by logos34 on 2008-07-09
> **Moey said:**
> 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7746    62219713+  83  Linux
/dev/sda3            7747        7779      265072+  82  Linux swap / Solaris 

Oh, no wonder you're having problems--swap is between root and the unallocated space!  The empty space has to be **contiguous** to the partition you're trying to enlarge.

Delete swap, make a new one at the end of the disk, then grow sda1 to take up the space.

Then mount root and edit /etc/fstab with new swap UUID:

sudo blkid

sudo mkdir /media/sda1

sudo mount -t ext3 /dev/sda1 /media/sda1

gksudo gedit /media/sda1/etc/fstab

---

### Post by Moey on 2008-07-09
Honesly logos, you are my hero tonite.

The worst part about this, is I though about that when staring at the partition manager, but i figured that the partition manager would be able to adjust to allow me to expand more, even though my swap space is "right next to" my partition.

But really, this just made my night.

Your the best =D>

---

### Post by logos34 on 2008-07-09
my pleasure! 

enjoy

> but i figured that the partition manager would be able to adjust to allow me to expand more, even though my swap space is "right next to" my partition.

unfortunately it can't do that...but who knows, someday soon it may be completely automated such that you will simply specify the arrangement you want, and presto!, it will move everything around for you!

---

