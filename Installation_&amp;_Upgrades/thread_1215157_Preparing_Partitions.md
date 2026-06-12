---
title: "Preparing Partitions"
date: 2009-07-16
forum: Installation &amp; Upgrades
---

### Post by Doggonit on 2009-07-16
After a long stint away from the world of *nix in all its flavors and shapes and sizes, I've decided to install Ubuntu 9.04 as I've heard nothing but good about it.

So, I've got a 1.4 GHz rig with 1GB of RAM and three hard drives as follows:

-One 120GB drive
-Two 40GB drives

I was thinking that I might install Ubuntu with all of its partitions on the 120GB drive, and then perhaps make one of the 40GB drives Windows XP or 7 or whatever, and finally make the last 40GB drive a shared NTFS drive so that I might share music and whatnot between the two OS's.

Anyway, focusing on the 120GB drive that I intend to install Ubuntu on, how do you recommend I partition it using the manual partition options? I've been desperately trying to find out what I need and don't need and here is what I gather I need to do:

```
/
``` The root partition: Apparently 5GB is recommended, should I perhaps make it 10? What really affects the space requirements here? And this will contain the following automatically:
```
/etc, /bin, /sbin, /lib and /dev
```
Is that correct? So I don't need to make partitions for those within the / one?

```
/usr
``` This contains user programs? What does that mean? Should I make it 10GB or 15?

```
/var
``` Variable data: Should I perhaps make this 5GB to be on the safe side?

```
/tmp
``` 2GB? How much do I need?
```

SWAP:
``` I do need to make a swap space as well, no? How much should that be? 2GB? 5?

```
/home
``` Apparently this can be all that's left of the 120GB. However, I've also read something to the effect that I need to leave at least 1GB as free space otherwise partition will fail (what?).


Is this it? I don't need anything more, or do I? I don't need to make a seperate /usr/local or do I? What sort of partitions should all of the above be? Primary or Logical? And do I always select the "Location for the new partition" as "Beginning" or "End"? I take it that except for the swap partition, I can make everything else ext3?


If my intended uses can help you to help me, I'll list them briefly: Web surfing, minimal image/photo editing (for website banners and logos and simple things like that), watching video (DVD's and perhaps high-quality internet feeds), some minimal programming (JavaScript stuff) and compiling, and some word processing and spreadsheet editing.


I hope this information suffices. In any case, I do know that all this should be fairly simple and straightforward, I'm just slightly unsure and at a loss at the moment.

---

### Post by merlinus on 2009-07-16
Why make things so difficult?

/ can be 10-15G, depending upon how many apps you intend to install.  /swap should be 1.5G at most, perhaps more if you want to hibernate.

You can leave the rest for /home, especially since you will be using one of your hdds as an ntfs partition for sharing data between linux and windows.

Creating a /data partition is another option, but I would forego separate ones for /var and such.

---

### Post by Doggonit on 2009-07-16
So, if I make a /data partition, do I make the / smaller? And how do I split the space between /data and /home?

I take it I would need:

/
swap
/home
/data

And I don't need to keep 1GB as free space? Also, should all of the above be Primary rather than Logical partitions?

---

### Post by merlinus on 2009-07-16
Since a hdd is limited for four primary, but almost unlimited logical, partitions, you may want primaries for / and /home, then an extended partition with logicals for /data and /swap.

My /data partition is much larger than /home, which is 20G.  / is 15G.

---

### Post by Doggonit on 2009-07-16
So would the following suffice? (The total size is 122941 MB)

/ -> 20,480MB (20GB) Primary
swap -> 2048MB (2GB) Logical
/home -> 30,720MB (30GB) Primary
/data -> 68,669MB (67GB) Logical
1024MB free

Or do I not need that free space?


ETA: So /boot, /tmp/, /var, and /usr will be in / and will be managed without requiring any further input on my part?

Also, do I need to install a boot loader now to permit me to install Windows in the future on one of the additional 40GB hard drives? Or will all that work automatically with the present setup?

---

### Post by merlinus on 2009-07-16
You will not need a separate /boot partition to run windows, even if on another hdd.  You can use map statements in /boot/grub/menu.lst.

Put the two primaries first, then the extended with the two logicals within that.  No need to leave unallocated space.

So the order will be:

/ - primary
/home -primary
extended
/data - logical
/swap - logical

Not to confuse things, but you could also put /home in a logical.

---

### Post by Doggonit on 2009-07-16
Thanks for the continued help. 

Final questions: Do I need that 1GB of free space to make the partitions (I read something to that effect) or is that nonsense and can I use up all the space?

I don't see any option for extended or otherwise, I can only select primary and logical, the size of the partition, the location (beginning or end), file system type (or swap or don't use space), and the mount point. 

I assume I don't need to bother beyond just making the / and /home first, as primaries, and then the other two and that's that, right?

---

### Post by merlinus on 2009-07-16
Yes.  No need to leave the free space, either.

---

### Post by Doggonit on 2009-07-17
Thank you very much for your help.

---

### Post by merlinus on 2009-07-17
Glad to be of service.  Let us know how it works out.

---

