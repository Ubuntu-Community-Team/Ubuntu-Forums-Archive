---
title: "Partitioning problems - resize extended partition?"
date: 2009-06-04
forum: Installation &amp; Upgrades
---

### Post by ScottHW on 2009-06-04
I'm helping my brother get Ubuntu on his new MSI Wind U100.  It comes with WinXP Home by default.  Strangely, MSI has decided that this means that the drive needed 3 partitions from the factory;
[LIST]
[*]one that appears to be some sort of recovery partition,
[*]then a "system" C: drive,
[*]then a "data" D: drive.
[/LIST]
He's opted for Ubuntu Netbook Remix (UNR).  When he originally went through the installation from a LiveUSB, he wasn't quite careful enough at the partitioning page(s).  So apparently what happened is he got an extended partition (b/c of 4 partition limit), and within it he got a little space as ext3 for root and a little space for swap.  Both need to be bigger.

So, in WinXP he decided to delete the D: partition and recreate it leaving ~30GB free space.  The idea was to just resize the Linux partitions with this free space.  But, that doesn't seem to be working.

Here's the output from fdisk -l  (displayed in CODE format for clarity)
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa8971d0b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         510     4096543+  12  Compaq diagnostics
/dev/sda2   *         511        5610    40965750    7  HPFS/NTFS
/dev/sda3            5611       15171    76798732+   7  HPFS/NTFS
/dev/sda4           19132       19457     2618595    5  Extended
/dev/sda5           19132       19435     2441848+  83  Linux
/dev/sda6           19436       19457      176683+  82  Linux swap / Solaris
```
And I've attached a screen cap of GParted (shows Linux partitions locked because this wasn't from the LiveUSB)

Thing is, I can't seem to resize the extended partition to include the newly free space.  Even when running from a LiveUSB, sda4 and sda6 still show "locked".

I've read some old forums, and some people thought that for one reason or another, you COULD NOT resize an extended partition, IF it's "to the right" of the available space.

But some have said that they were able to use GParted to resize their extended partitions.

Anybody know the facts on this, and why?

Since there isn't any data with Ubuntu yet, there is the possibility of just blowing away the extended partition and the ext3 + swap and starting over and using the free space.
I just want to know what the deal is, for my learning as well as for others'.

---

### Post by listener on 2009-06-04
Right off, I'm not sure what you can do with parted 
on this.  If it is not inconvenient, I'd go ahead and
delete the volumes in the extended partition and start
over.  I'm not saying you cannot, I don't know.

Another option is to get a (non-os-specific) partition
manager type software, to do the job.  I use and trust
Bootit NG (I suppose its ok to mention the name of a 
product here).  It is very good software, and in fact
you can use it for free, you simply cannot install it
for more than 30 days.  However, you can put it on a
cdr and use it for partition management, just not
boot-management and other features which require
installation.

Bootit NG is extremely powerful, however, which makes it
pretty potentially dangerous if you don't know what you
are doing.  I still think in your case you may be better
off deleting the extended partition and recreating it.

The 'right of' part, simply means that the volumes you
have inside the extended partition are at the end, so
it is a problem to resize 'backwards'.  (You wouldn't
grow backwards - heh - growing generally occurs forward)

Good Luck

---

### Post by zman58 on 2009-06-04
You should delete sda4 sda5 and sda6. Then run through the Ubuntu install again. It should use the free space on the hard drive and will utilize the 30.34gb and also the space you free up by deleting sda4,5,and sda6.

Additionally you could resize (from the end) the Windows data partition sda3 to get some data from that into the free space as well before you begin with the Ubuntu install.

---

### Post by merlinus on 2009-06-04
If you decide to resize your windows partition, be sure to get rid of any temp files and defrag beforehand.

Then you could reinstall ubuntu, setting up an extended partition after the windows one with all remaining space, and create / and /swap as logical partitions within that.

If there is enough room, you might also consider creating a /home partition as well, and I would place /swap once again at the end of the hdd.

---

### Post by pbacco on 2009-06-05
Have you tried using only parted in CLI ? Gparted won't let you resize the partition.

Use:

sudo parted /dev/sda

resize and answer the questions

Hope it helps,

Regards

---

