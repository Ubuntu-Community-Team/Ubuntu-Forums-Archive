---
title: "Making new partitions for linux OS"
date: 2016-03-03
forum: Hardware
---

### Post by damian22 on 2016-03-03
Hi I am a new Linux user, I love it so far and dont understand why I didn't make the switch before

Now I dual booted my computer to keep my windows license active but doing the dual boot I didn't give enough space for my Linux, I have 500 gigs of space but I only gave 15 gigs to linux (stupid mistake). Now when I run disk space I see that Linux has 15 gigs available and that my os which has windows has 475 gigs available with only 55 gigs used. I almost maxed my 15 gigs on linux.

Is there an easy way to free up space from windows os and assign it to linux ( say 300 gig ) 

Thanks for a great community

---

### Post by weatherman2 on 2016-03-03
It would be fairly easy for an experienced user to do this.  Here's how I would do it if I wanted to avoid re-installing (assuming the Linux installer put the 15GB Linux partitions at the end of the drive and Windows at the beginning): I would backup the Linux OS partition to another disk, then delete all the Linux stuff; then resize the Windows partition to free up as much room as I wanted; then make new, larger Linux partitions (new swap partition, too), then restore the backup I made.

For a new user, this is way too complicated.  It's going to be easier for you to start over - erase Linux, resize your Windows partition (use Gparted - but be SURE to back up any files you care about, because very rarely a resize goes wrong and you could lose data, but usually it's pretty safe.  Better safe than sorry!), then re-install Linux from scratch in the larger free space.

The complication for you is how to resize your Windows partition.  The installer probably did this for you automatically the first time.  I'm not sure it would do it again if you just re-booted the installer disk or USB but you can try.  If it doesn't work automatically, boot a Linux live CD or USB and start up GParted (partition editor).  You can delete your Linux partitions (once you've copied off any files you had saved in Linux - deleting your partitions erases everything in Linux, of course!), then delete the Extended Partition (if Linux made one for your Linux partitions).

Then, shrink your Windows partition from the END to make free space, using Gparted.  This should be easy, but it could take some time (probably not if it is mostly empty as you say).

If you want more specific guidance about your current partition scheme, open a terminal now and type this command:

```
sudo parted -l
```

and post the results here.  Then we can say, "Get rid of these partition(s) and shrink this one, etc."

---

### Post by damian22 on 2016-03-03
Number  Start       End            Size         File         system                Name                          Flags
 1             1049kB  525MB       524MB    fat32      EFI system              partition          boot, esp
 2            525MB    567MB       41.9MB    fat32     Basic data partition     hidden
 3             567MB    701MB      134MB    Microsoft reserved partition          msftres
 4              701MB    1488MB    786MB    ntfs        Basic data partition          hidden,   diag
 5              1488MB   474GB      473GB    ntfs        Basic data partition         msftdata
 7               474GB    486GB      11.9GB    ext4
 8              486GB     490GB      4172MB    linux-swap(v1)
 6             490GB      500GB      9827MB    ntfs       Microsoft recovery partition  hidden, diag


So if I wanted to go for option one I would save every partition on a disk and then delete every partition expect 3, 5, 6. And then resize partition 5 since it is the one with 473 gig

Do you know if there is a step by step guide somewhere for something like this?

---

### Post by weatherman2 on 2016-03-03
OK, that must be a GPT partition table - easier to deal with.  But you'll still have to delete partitions #7 and #8 - the Linux partitions - then shrink partition #5.  Then re-install.

One other way to avoid re-installing if you could live with gaining just 4GB is to delete your swap partition #8, shrink #5 by 4GB, make a new swap partition in the free space, then grow #7 by the 4GB of space you freed up after that.  You can do this all with Gparted (from a live boot), but you would need to edit your /etc/fstab file to change the reference to the new swap file.

Either way - I repeat: BACK UP your data first!  Resizing partitions is always very slightly risky.  If you have a USB backup drive available with some free space, I would use Clonezilla to back up the entire disk (including Windows).  Then you could always revert your drive to the way it is now in case of a glitch or a mistake because you are new at this stuff.  The backup won't take nearly the full 500GB of space on a USB drive, because you said your Windows partition is mostly empty.  Clonezilla will save only used data and compress everything.  You can install Clonezilla on a boot USB drive and boot it that way.

---

### Post by Bucky Ball on 2016-03-03
What you would do is use Windows tools to shrink number 5 then boot from live Ubuntu install media, get to a desktop and expand the Ubuntu partition (7) into the free space you've created. That's it.

However, thing is, your EXT4 partition number 7, which must be your Ubuntu as you have no others, shows you've only used 11.9Gb of 486Gb so I'm a bit confused ... :-k

PS: You should consider using symlinks. You have a lot of space there and you probably already have plenty of data stored on those partitions. It is fairly simple to link the folders in your /home inside the / partition to folders on other partitions, even NTFS partitions. 

I generally install Win to 40-50Gb, Ubuntu to 15-20Gb, then create a small NTFS partition for sharing data between the two. Common practice. I have about four Ubuntu installs but their /home partitions are linked to a large EXT4 /data partition (rarely use Windows).

---

### Post by Dennis N on 2016-03-03
Yes, you should definitely use Windows disk management tools for shrinking the ntfs partition. And then you should be able to expand #7 into the space created using gparted working from live media. Again, back up user data before any partition resizing.
@BB
11.9 gB is indicated as the size (total space) of partition #7.

---

### Post by Bucky Ball on 2016-03-03
Ah, my mistake. In that case, first paragraph in my last post is about it.

---

