---
title: "Convert NTFS external drive"
date: 2006-11-10
forum: Hardware &amp; Laptops
---

### Post by Abb on 2006-11-10
Hello world.

Actually, I've just installed Ubuntu Edgy Eft on my Acer 5670 laptop, I solved my screen and wifi problems, but I need your help concerning external drives. I have a 250GO Iomega external drive, USB 2.0, and it is in NTFS, so I can't write files. i'm looking for advice: is it secure to mount NTFS drives under linux (some says it is risky)? Or, if I choose to convert my whole drive to linux system, will it be possible to write/read from windows computers (in FAT32, I think yes, but...), and at least, how to convert NTFS drive to FAT32?
Thanks to all, and forgive my bad english (i'm french) and my noobiness.

M.L.

---

### Post by kidders on 2006-11-10
Hi there,

Your english is fine :-) You'll need to reformat your zipdisks to convert them to FAT32. You can write to NTFS if you want, but there may still be glitches in the reverse-engineered implementation of it ... so you might lose data!

---

### Post by boban on 2006-11-10
> **Abb said:**
> 
Actually, I've just installed Ubuntu Edgy Eft on my Acer 5670 laptop,


Welcome and enjoy :)

> **Abb said:**
> 
I solved my screen and wifi problems, but I need your help concerning external drives. I have a 250GO Iomega external drive, USB 2.0, and it is in NTFS, so I can't write files. i'm looking for advice: is it secure to mount NTFS drives under linux (some says it is risky)? Or, if I choose to convert my whole drive to linux system, will it be possible to write/read from windows computers (in FAT32, I think yes, but...), 


I'm not an expert myself, but I've been mounting (read only with no exec) NTFS partition for quite some time and never had any problem with it. You can read/write fat32 and [ext]("http://www.fs-driver.org/") (never tried ext reading by myself but I heard it is reliable). There are way's for read-only access reiserfs partition (f.e. via total commander plugin). 

> **Abb said:**
> 
and at least, how to convert NTFS drive to FAT32?


I might been wrong with that but I think you have 3 options for that:
[LIST]
[*] Format drive under windows - you can do it from Control Panel / Administration Tool/ Disk Management (sorry if I named something wrong, I don't use windows often now)
[*] use gparted (you can install it from repositories)
[*] use fdisk (hard!)
[/LIST]

Personally I would recommend splitting your hard drive into some partition - some purely linux, some for access with windows...(but I'm not sure if your external drive is seen as normal hdd or something else, somebody should correct me if I'm wrong...)

---

### Post by kidders on 2006-11-10
Hey again,

Just a minor clarification...

Gparted and fdisk are disk partitioners, in that they let you create partitions, not filesystems. Creating a FAT32 filesystem on a partition that previously held an NTFS one is normally a matter of typing **mkfs.vfat /dev/whatever**

Boban's suggestion of using multiple filesystems on the same removable device can be very handy. Unfortunately, Bill Gates has decided that no-one should ever want more than a single partition on a device that isn't screwed into a computer. As a consequence, Windoze often won't recognise 2nd and subsequent partitions on a large number of removable devices ... although Linux is happy to :-)

---

### Post by boban on 2006-11-11
> **kidders said:**
> 
Gparted and fdisk are disk partitioners, in that they let you create partitions, not filesystems. Creating a FAT32 filesystem on a partition that previously held an NTFS one is normally a matter of typing **mkfs.vfat /dev/whatever**

Thanks for clearing that out:)

> **kidders said:**
> 
Boban's suggestion of using multiple filesystems on the same removable device can be very handy. Unfortunately, Bill Gates has decided that no-one should ever want more than a single partition on a device that isn't screwed into a computer. As a consequence, Windoze often won't recognise 2nd and subsequent partitions on a large number of removable devices ... although Linux is happy to :-)

So 1st partition for shared data with windows, others - for linux only :]

---

### Post by bobpaul on 2006-11-11
> **Abb said:**
> and it is in NTFS, so I can't write files. i'm looking for advice: is it secure to mount NTFS drives under linux 
There are various methods for writing files to NTFS, but only 1 is not considered beta: [Captive-NTFS](http://ubuntuforums.org/showthread.php?t=10175). Unfortunately it's slow--especially for large files--and no longer maintained, but it's what I would feel safest using if I were going to use anything. Captive uses the windows NTFS driver on a compatibility layer, like wine.

Another alternative is [NTFS-3G](https://wiki.ubuntu.com/ntfs-3g?highlight=%28ntfs%29). This is considered beta, but is supposedly pretty stable. This one is implemented in such a way that if it can't safely do something it will just error and not do it rather than corrupting. Sounds pretty good to me. Also, since it's a direct implementation of NTFS, and not running the windows binaries on a compat-layer, it's very responsive.

I think it would be safer to setup the drive as Ext3 and use an ext3 driver for windows.

> Or, if I choose to convert my whole drive to linux system, will it be possible to write/read from windows computers (in FAT32, I think yes, but...),

Yes. There are two very good options that I've used frequently. [Ext2fsd](http://ext2fsd.sourceforge.net/) and [Ext2IFS](http://www.fs-driver.org/). Both support full read/write support for Ext2/3 systems. Both treat Ext3 systems as ext2, however (just like older versions of linux would) so that means no journaling.. if a crash occurs while writing your more likely to corrupt without journaling, kind of like the days of Win98 etc on Fat32. I'd recommend Ext2IFS, it's easier to use.

> and at least, how to convert NTFS drive to FAT32?
You can't, at least not easily. Also, I don't think Fat32 supports things like large files (ie, those over 2GB) so that could be a problem if you want to store things like DVD images on your external drive. I would recommend Ext3 on the drive and Ext2IFS to read it from Windows.

If you do want to try to convert the drive to something else, here's how I would do it. [LIST=1]
[*] Install QtParted if you use Kubuntu or GParted if you use Ubuntu. 
[*] Move as much of the data off the drive as you can. 
[*] Now use Qt/GParted to shrink the NTFS partition that's on the drive.
[*] Create an Ext3/Fat32 partition in the freespace you just created.
[*] Mount your new partition and copy data to that new partion until it's full.
[*] Repeat steps 3-5 until the NTFS partition is empty
[*] Delete the NTFS partition and create an Ext3/Fat32 partion where it used to be. This is your final partition.
[*] Copy data off the extra partitions you created earlier onto the final partition to empty one of the temporary ones.
[*] Delete the temporary partition you just freed and expand the final partition
[*] Repeat steps 8-9 until you only have the final partition you wanted.
[/LIST]

_Some things to keep in mind:_
[LIST]
[*]You can't change the starting point (ie, move) anything other than a Fat32 partition. NTFS and Ext2/3 partitions can be resized, but only by moving the end. I would recommend making all temporary partitions the same size as the first temp partition you create and clear them in the reverse order you created them.
[*]If there are more than 4 partitions the remaining partitions must be placed inside of an Extended Partition. It would probably be wise to create the extended partition to hold all of your temporary partitions. You will need to unmount all logical partitions (those within the extended) in order to resize the extended partition.
[/LIST]
I've done the above quite frequently, and it's really my preferred method of doing this sort of thing. M$ has a tool that will convert Fat32 to NTFS, but not the other way and I know of no other tool, so this really is the way to do it.

It would be a LOT easier to just backup the entire drive and reformat the whole thing in one shot to Fat32/Ext3.

---

### Post by Abb on 2006-11-11
Thanks a lot everybody.
So I've made a backup of all my files, I can erase and reformat my external disk, but in gparted, the button isn't clickable... how can I force to format?

---

### Post by coffeecat on 2006-11-11
It's probably because the drive is still mounted - you can't erase/reformat mounted partitions. First of all make sure you are showing your external drive by selecting it in the drop-down box at top-right. It'll probably be /dev/sda. Now highlight the partition you want to change. If the buttons are still greyed out select the 'Partition' menu and then unmount. You should now be able to erase and reformat.

If you are still having problems you may need to set a disklabel first. You can do this under the menu entry 'Device'.

---

### Post by Abb on 2006-11-11
It's done!
thanks a lot to all of you.
M.L.

---

