---
title: "using linux to 'swap' two hard drives"
date: 2009-12-03
forum: Hardware
---

### Post by nuclearpidgeon on 2009-12-03
hey there

I have 2 PC's, one with a 250GB hdd and the other with a 320GB hdd. Recently it has become apparent that it would make more sense to have the 320GB in the other computer, due to running out of space (too many damn operating systems!)

So I want to transfer the files between hard-drives whilst not having to re-install the OS. I have a 500GB external hard-drive which I used in conjunction with 'dd' to make an image of each drive (dd if=/dev/sda | gzip > /media/Seagate/image.gz). However, because they are both different sizes, I realized that this probably wont work.

Am I correct in saying this? If so, is there some other way to swap the data on the disks? Both hard drives have one NTFS partition with Windows XP on it (I removed all other OSes a while back due to space restrictions), so it really needs to be a proper image, because Ubuntu/Nautilus copies don't save Windows' hidden/system attributes of files

thanks in advance

---

### Post by Fire_Chief on 2009-12-03
You probably want to check out CloneZilla [http://www.clonezilla.org]("http://www.clonezilla.org")

And it seems you only need to use the external drive for one of the images...

320GB -> image to external
250GB -> clone to 320GB
external -> push image to 250GB

The only tricky part will be the 320 -> 250 change. Hopefully your filesystem currently on the 320GB drive is not using more than 250GB of space else it will not fit (of course).

I think there's still some gotchas in here but I've not done shrink operations via cloning before. Expansions are easy.

Hope this helps,

---

### Post by seeker5528 on 2009-12-03
Going from larger to smaller is not supported.

I would clone 350 to the 500 first, resize the partitions with gparted so they are small enough to fit on the 250, then boot from it to check things out and make sure they are working.

Once the resizing is done, then it should be no problem to clone the 250 to the 350, then the 500 to the 250, then expand the partitions to fill the disks.

I have had mixed results booting Windows on cloned drives when using Clonezilla, so you want to verify things are working each step of the way.

If Clonezilla fails me, then I normally fall back to ddrescue, which I run from [System Rescue CD](http://www.sysresccd.org/Main_Page)

ddrescue *infile outfile*

```
ddrescue /dev/sda /dev/sdb
```

As long as the partitions are pre-shrunk and at the beginning of the drive, going from a larger drive to a smaller one should not be a problem, ddrescue will quit when it runs out of space at the destination.

You can use fdisk to verify the drives are showing up as you expected.

```
fdisk -l
```

Later, Seeker

---

### Post by nuclearpidgeon on 2009-12-03
> **Fire_Chief said:**
> 
And it seems you only need to use the external drive for one of the images...

320GB -> image to external
250GB -> clone to 320GB
external -> push image to 250GB


Oh yeah, forgot to mention that: both drives are SATA, and there's only one SATA power connector in each PC... so no go, I have to use the500GB to hold BOTH images, as copying across the network would probably be slower and riskier anyway

so, heres what I'm going to do next, just for clarification and checking:

[LIST=1]
[*]delete both dd .gzip HDD backups off 500GB external HDD
[*]using GParted, shrink the 320GB partition to as small as possible to make things easy and fast (there's only about 100GB of stuff on there anyway)
[*]use CloneZilla to copy the partition off the 320GB to the external HDD
[*]use CloneZilla to copy the partition off the 250GB to the external HDD
[*]use CloneZilla to move the smaller 320GB image onto the 250GB HDD
[*]check to see if it boots all hunky-dory
[*]use CloneZilla to move the 250GB image
[*]Free Space Party!!!
[/LIST]
any problems/suggestions/comments with that method?

---

### Post by seeker5528 on 2009-12-04
That sounds like it should work.

You do know that adapters to go from the larger power connection to SATA are dirt cheap right? :p

Later, Seeker

---

