---
title: "Reformat external HDD"
date: 2007-01-20
forum: Hardware &amp; Laptops
---

### Post by SteveHoffmanUK on 2007-01-20
Ubuntu 6.06 Dapper. Relative newbie, but happy Ubuntu user.

I have a 80GB Freecom FHD-2 Pro external hard disk which I use for backup security, but have problems writing files to it. Discovered it's formatted in FAT-16. Don't know why.

I want to reformat it to EXT3 but GParted doesn't recognize it. Can someone tell me how to either:
1. Get GParted to recognise it, or
2. Use another program to reformat it?

Don't mind losing the data on it. 

Also, my System, Computer display shows two devices:
1. FHD-2PRO with a little red symbol beside it, whose meaning I know not and
2. fhd2-pro

I tried deleting (2) above but Ubuntu won't permit this.

Looks to me as if my external hardware setup is badly screwed up. What is the best way of cleaning up this mess?

---

### Post by meng on 2007-01-20
Can you:
sudo fdisk -l

and thereby identify which /dev/hd? or /dev/sd? corresponds to this hard drive?

---

### Post by SteveHoffmanUK on 2007-01-20
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9729    78148161    6  FAT16

```

---

### Post by meng on 2007-01-20
Ok, so I take it /dev/sda is the external hard drive, and /dev/sda1 is the only partition on it.

First, make sure the partition is unmounted:
sudo umount /dev/sda1

then, it's time to reformat it!
mke2fs -j /dev/sda1
(mke2fs means make an ext2 filesystem, the -j switch enables journaling which means it's ext2+journaling = ext3)

Now you have an ext3 partition.

EDIT: you may need to
sudo mke2fs (blah, blah)

---

### Post by SteveHoffmanUK on 2007-01-20
Thanks, Meng. Looks like it worked, but check it out, as I haven't a clue:
```
steve@steve-desktop:~$ sudo umount /dev/sda1
steve@steve-desktop:~$ mke2fs -j /dev/sda1
mke2fs 1.38 (30-Jun-2005)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
9781248 inodes, 19537040 blocks
976852 blocks (5.00%) reserved for the super user
First data block=0
597 block groups
32768 blocks per group, 32768 fragments per group
16384 inodes per group
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000, 7962624, 11239424

Writing inode tables: done
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 24 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.

```

---

### Post by meng on 2007-01-20
Yeah that's good.
Try
sudo fdisk -l
again

---

### Post by SteveHoffmanUK on 2007-01-20
Hmm, I think I spoke too soon:
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9729    78148161    6  FAT16
steve@steve-desktop:~$

```

So what happened? Or, what DIDN'T happen? :)

---

### Post by meng on 2007-01-20
Reboot?

---

### Post by SteveHoffmanUK on 2007-01-20
Rebooted, but got:
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9729    78148161    6  FAT16

```

---

### Post by meng on 2007-01-20
Curious, I must admit I always do my repartitioning using a Live CD. There is a GParted Live CD which is perfect for this purpose.

---

### Post by SteveHoffmanUK on 2007-01-20
Oh Gawd, I suppose I have a live CD somewhere .....

BUT, if GParted doesn't recognise my HDD now, why would it do so using a live CD?

ON EDIT: Let me get this straight, do you mean a live CD of Dapper or a live CDof GParted (if there is such a thing)??

---

### Post by meng on 2007-01-20
For whatever reason (somewhat more technically proficient could explain) repartitioning doesn't always "take" when running in installed mode. You could use either a Dapper Live CD or a GParted LiveCD (I use the latter because it's an updated version of GParted and has more functionality):
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by SteveHoffmanUK on 2007-01-20
Thanks, Meng, I really appreciate your help on this. 

Sounds to me like I'd be better off burning a live GParted CD - wouldn't have all the other stuff on it for Ubuntu.

Will try it and report back.

---

### Post by maumau on 2007-01-20
> I want to reformat it to EXT3 but GParted doesn't recognize it.
have you try to fetch up in GParted options  (Ctrl+R) after linkage of the external dev

---

### Post by SteveHoffmanUK on 2007-01-20
maumau wrote:
> have you try to fetch up in GParted options (Ctrl+R) after linkage of the external dev

Afraid I don't understand. My GParted doesn't have any "options" that I can see. What do you mean by "external dev"? Sorry, but I am a newbie and can't cope with much technical stuff.

---

### Post by SteveHoffmanUK on 2007-01-20
Hey, something weird happened when I rebooted - just noticed. On my desktop, the icon FHD2-PRO has been replaced by an icon for usbdisk, and I now seem to be able to copy my Home folder without any problems. Don't understand.:confused:

---

### Post by meng on 2007-01-20
> **SteveHoffmanUK said:**
> Hey, something weird happened when I rebooted - just noticed. On my desktop, the icon FHD2-PRO has been replaced by an icon for usbdisk, and I now seem to be able to copy my Home folder without any problems. Don't understand.:confused:
Heehee maybe you had to reboot more than once to get it to work ... or maybe Ubuntu was just slow to realize that something had changed.

---

### Post by SteveHoffmanUK on 2007-01-20
No, I'm talking about my only reboot - I've only done one. The desktop and Nautilus GUI icons have changed, but I still get the same results from sudo fdisk -l, that is:  FAT-16.

Well, my GParted live CD has now downloaded, so I'll have a go.

---

### Post by DerHesse on 2007-01-20
Your 80gb FAT will probably not work with windows, but ext3 wouldn't either :lolflag:

---

### Post by SteveHoffmanUK on 2007-01-20
Der Hesse wrote:
> Your 80gb FAT will probably not work with windows, but ext3 wouldn't either

Windows? What's that?:lolflag: 

OK Guys, here's the story:

I burned a live CD of GParted, ran it, and my HDD (dev/sda1) shows as a single EXT3 partition. Magic - that's just what I want. Only thing is, when I do a sudo fdisk -l, I get this:
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9729    78148161    6  FAT16
steve@steve-desktop:~$

```

As you Americans say, "Go Figure!" I can't. :confused:

---

### Post by meng on 2007-01-20
Just ignore it and start putting data on the drive. Maybe sudo fdisk will realize the change later on.

---

### Post by SteveHoffmanUK on 2007-01-20
meng wrote:
> Just ignore it and start putting data on the drive. Maybe sudo fdisk will realize the change later on.

Good advice. I did that, and I must say the copying went smoother than it ever has before, so I'm going to assume all is well.

Thanks again for all your help. Ubuntu and its forums really star. =D>

---

### Post by DerHesse on 2007-01-21
> **SteveHoffmanUK said:**
> As you Americans say, "Go Figure!" I can't. :confused:
There is no proof of anyone from US+A in this thread. :biggrin:

---

