---
title: "Partitioning"
date: 2007-04-05
forum: Hardware &amp; Laptops
---

### Post by renators on 2007-04-05
hello, here is my problem:

I have one 200gb hd formatted with ntfs and currently disk usage is about 100gb. I want to make it ext3, but i don't want to lose any data so I've been thinking if I could just format the free space using ext3 then move the files from the ntfs partition to the ext3 one (using ubuntu with the ntfs-3g drivers) and then making the now free ntfs partition ext3.

So the big deal here is I'm afraid that I can damage my hd doing it. Is there anyway to damage my hd making the free space ext3, moving the existing files to the new ext3 partition and then making the free ntfs space ext3?

Thanks in advance for your help.

ps: i don't know if it can help it's a 7200 ide seagate.

---

### Post by jjordan on 2007-04-05
Define "damage":) .  I have reformated hundreds of drives with a wide variety of file systems and never damaged the physical drive.  There is of course a danger of losing data.  Most of the time I have lost data it was due to my getting confused about which drive or partition contained what.  If you have another drive that can hold the data, or a friend has an external that you can borrow, it would be better to copy the contents, format the entire drive and copy it back.  If that is not possible then make sure you run chkdsk on the NTFS drive and defrag it several times (XP defrag is lazy) before you try to shrink the partition.  In theory it should be possible to:

1.) shrink the NTFS partition
2.) create a new EXT3 partition
3.) copy the existing data to the EXT3 partition
4.) delete the NTFS partition
5.) expand the EXT3 partition to fill the drive.


**If it is at all possible BACK UP any important data before you do this!  If nothing else it would be worth the price of a few blank DVDs to be safe.**

-j

---

### Post by az on 2007-04-05
> **renators said:**
> 
So the big deal here is I'm afraid that I can damage my hd doing it. Is there anyway to damage my hd making the free space ext3, moving the existing files to the new ext3 partition and then making the free ntfs space ext3?


No.  Partitioning is just normal use.  In the same way you write, read and rewrite to blocks on the disk when you save data on it, you do the same to the partition table when you change it.  Whether you partition your drive every day or only once in it's lifetime, it will last the same amount of time.


Dropping your hard drive from eight or nine feet in the air onto hardened concrete will significantly reduce the lifespan of the drive, though.  Don't do that.

---

### Post by renators on 2007-04-05
I would, for sure, make some backups if i could. I just don't have a dvd-rw and my cdrw is broke. so i'm pretty ******. I hope it works that way, I've already defragged my hd and i'm ready to go.

Wish me luck.

I'll post soon to let you know if i've succeed in my task.

Really thanks for your help.

---

### Post by renators on 2007-04-05
ohhh. i was thinking about dropping my hard drive. SUCK! i will never buy computer related things again, since i can't throw it against the wall.

---

