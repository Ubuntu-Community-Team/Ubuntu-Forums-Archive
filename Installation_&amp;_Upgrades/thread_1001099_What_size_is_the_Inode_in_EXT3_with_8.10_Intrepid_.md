---
title: "What size is the Inode in EXT3 with 8.10 Intrepid ibex"
date: 2008-12-03
forum: Installation &amp; Upgrades
---

### Post by DWade on 2008-12-03
](*,)I would like to know what size the Inodes are in Ext3 as formated by either Kubuntu or Ubuntu in new 8.10. (are they 128 or 256)  I am having some issues with my Acronis backup software with the ext3 partition.  

In a fresh loaded Ubuntu or Kubuntu ready for 1st boot with a partition grub boot, I go to a windows partition or I will put in the arconis cd and backup the partition.  I can now at any time re-load the partition and use the alternate cd in repair a broken system mode and reinialize grub.:p

The version of acronis I use is 9.  10 and 11 elevate the windows explorer to view backup files, and if your searching for something and backup files are there it, continues to search thru each backup. This can cause the search to become expressively long and useless. (Especially if you forgot where exactly you placed a backup file):-x
  
Acronis says the partiton is damaged. It will have to back it up sector by sector.  That means the image file that should only be about 1.9 gigs is now almost as big as the partition. With a 40 gig partition this is no good.:(

To fix the problem I reformated the partition with system commander as EXT3 and then loaded Ubuntu on one computer and Kubuntu on the other.

---

### Post by caljohnsmith on 2008-12-03
Intrepid uses a 256 byte inode size compared to Hardy and previous releases that use a 128 byte inode size. You can check the inode size of your ext3 partitions by doing:
```
sudo dumpe2fs /dev/sdaX | grep -i "inode size"
```
And replace sdaX with the partition in question.

---

### Post by DWade on 2008-12-03
:p Thanks

That creates a problem major.:icon_frown:
ext2ifs will not work with inodes of 256.  
Niether does acronis.  

So this is bug in the alternate CD.  It needs a choice of making the partition inodes either 128 or 256.:frown:

In my case I need 128 bit inodes. I can read and write ext3 but I can not write to rieserfs.  Reiserfs for some reason does not like to accept a grub partition boot.  It take 2 to 3 times writing grub to /dev/sda(x), to initialize a partition boot.
Live CD will never create a partition boot with rieserfs because you can only write to it once.  With the alternate cd you can write un til the red screen disappears.


Thanks 

I will check with acronis and see if version 2009 can read and write to 256 bit inode

---

### Post by caljohnsmith on 2008-12-03
Have you tried using [ext2FSD]("http://sourceforge.net/projects/ext2fsd") instead? It supports the new 256 byte ext3 partitions.

---

### Post by DWade on 2008-12-08
:confused:First Just being able to view, read, and write in windows is only part.

As I stated I use Acronis backup software. As of version 2009 it does not read 256 bit ext 3 partition (or is it ext4).  I backup up my whole partition(s). 

That allows me to experiment and try diferent things or setting or drivers.  If it goofs it up. I restore the partition.

Then I Put in the Alternate CD select repair broken system and reinitial grub from the CD.  I use a partition boot, in my linux partition because I have been using the program System commander since 1992 or 1993. I prefer that to grub, since I format, move create resize or whaterver to a partition upon boot.

Acronis will only sector to sector backup EXT3 256 bit.  Which changes a 2 gig backup to 12 gig the size of the partition.

---

