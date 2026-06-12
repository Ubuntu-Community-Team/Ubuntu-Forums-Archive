---
title: "8Gb USB drive becomes corrupt after 2Gb"
date: 2008-08-27
forum: Hardware
---

### Post by moshuptrail on 2008-08-27
I recently acquired an 8Gb thumb drive and it worked great until I tried to add enough files to exceed about 2Gb.  Maybe 3Gb, I can't be sure, but the bottom line is that at some point the directory becomes corrupt.  The files and directories change and the drive becomes useless.

Any ideas?  I have not seen this posted by anyone else. 
I've seen some postings about thumb drives that are not detected.  This one is fine that way and works perfectly until it gets filled to a certain point.  Then everything suddenly becomes corrupt - as if the index were corrupt.

ps. I can reformat the drive on a windows pc and it's fine again.

---

### Post by Comzee on 2008-08-27
Have you tried reformatting the flash drive as fat32, or any other file system that you like?

---

### Post by moshuptrail on 2008-08-27
Yes.  I reformat in Windows and it works fine until I use on Linux again and fill past that magic point.

---

### Post by Comzee on 2008-08-27
Install Gparted and your linux mahine. start up the program. ```
gksudo gparted
``` Go to divices, and switch to your flash drive. Unmount it using gparted. Reformat it using the ntfs file system. If that doesn't work you can try using the ext3 file system, but then the flash drive wouldn't work in windows.

---

### Post by moshuptrail on 2008-08-27
You think NTFS will hold 8Gb, while fat32 will not?

At this moment I've got it on a Windoze machine and I'm filling it with files to make sure it will take 5Gb - and make sure it's not a hardware problem.  Then I'll try your idea.

---

### Post by moshuptrail on 2008-08-27
Well, Windows XP was able to put 4.2Gb on the drive with no ill effects.  Linux can read the drive.

Gparted sees the drive on /dev/sdb and shows 4.16Gb used..  

BUT, when I unmount the drive, gparted tries to rescan and just sits there re-scanning forever.  The only way to stop it is to unplug the thumb drive.

Didn't see THAT coming!

---

### Post by Comzee on 2008-08-27
I've had issues with gparted just sitting there scanning forever. I've had to wait for 15 minutes, and finally would would detect the drives. Let is sit there, go do something for awhile and come back to it, if it's still not detecting the drive then you might have a problem.

---

### Post by moshuptrail on 2008-08-27
Finally got it formatted as ext2 (ntfs grayed out)
But now I can't place files on it.  "Permission Denied"

---

### Post by moshuptrail on 2008-08-27
Whoa!

Check this from dmesg:

> [ 7871.176087] EXT2-fs error (device sdb1): ext2_new_blocks: Allocating block in system zone - blocks from 295426, length 1
[ 7873.393493] EXT2-fs error (device sdb1): ext2_new_blocks: Allocating block in system zone - blocks from 295428, length 1


---

### Post by Comzee on 2008-08-27
Use gksudo nautilus then go to your /media directory (where the usb drive will be mounted) and you will have permission to put stuff on it. But as ext2, as I said your flash drive won't work in windows.

---

### Post by moshuptrail on 2008-08-27
Well, I am thinking now that the drive is defective.  Not sure why windows has no problems with it, but this is what I get from dmesg after copying lots of files to it:

> [ 8146.965072] EXT2-fs error (device sdb1): ext2_new_blocks: Allocating block in system zone - blocks from 1114363, length 1
[ 8146.967454] EXT2-fs error (device sdb1): ext2_new_blocks: Allocating block in system zone - blocks from 1114365, length 1
[ 8252.610904] EXT2-fs error (device sdb1): ext2_check_page: bad entry in directory #121560: unaligned directory entry - offset=0, inode=65569188, rec_len=55593, name_len=6
[ 8252.613894] EXT2-fs error (device sdb1): ext2_readdir: bad page in #121560
[ 8252.624904] EXT2-fs error (device sdb1): ext2_check_page: bad entry in directory #121441: rec_len is smaller than minimal - offset=0, inode=0, rec_len=0, name_len=0
[ 8252.626757] EXT2-fs error (device sdb1): ext2_readdir: bad page in #121441
[ 8252.678673] init_special_inode: bogus i_mode (160277)
[ 8254.486859] EXT2-fs error (device sdb1): ext2_readdir: bad page in #121560
[ 8260.188365] EXT2-fs error (device sdb1): ext2_readdir: bad page in #121441
[ 8261.605782] EXT2-fs error (device sdb1): ext2_readdir: bad page in #121441
[ 8269.276327] EXT2-fs error (device sdb1): ext2_readdir: bad page in #121441
[ 8269.278863] EXT2-fs error (device sdb1): ext2_readdir: bad page in #121560
[ 8342.272065] EXT2-fs error (device sdb1): ext2_readdir: bad page in #121560
[ 8344.993588] EXT2-fs error (device sdb1): ext2_readdir: bad page in #121441
[ 8443.760551] EXT2-fs error (device sdb1): ext2_readdir: bad page in #121441
[ 8443.762643] EXT2-fs error (device sdb1): ext2_readdir: bad page in #121560


---

### Post by Atsuko on 2008-08-27
Did you happen to buy this on ebay?
There has been some people selling them that are not the size they are.
When you go to use them you find files are bad from the wrong size.

---

### Post by moshuptrail on 2008-08-27
This was from eBay.  $20 
So how would I know if the size was wrong?  Gparted is reporting 8Gb.  If it was 4Gb I could still use it, but I'd have to fix it somehow.

---

### Post by youknowwhat4q on 2008-08-27
Might not be too helpful for you, but I had the same problem with a 4GB and I just partitioned it and it was fine.

Mine was because the versions of windows didn't properly support the firmware on the flashdrive.

---

### Post by moshuptrail on 2008-08-27
Come to think of it, I may have exactly the opposite problem.  I can load this drive up from windows with no problem, but write access from Linux corrupts the drive.

---

### Post by Atsuko on 2008-08-27
Watch the left side and you will see the warnings down at the bottom.
[http://shop.ebay.com/items/_W0QQ_fromZR46?_nkw=flash+drives&_fromfsb=0&_trksid=m270.l1313](http://shop.ebay.com/items/_W0QQ_fromZR46?_nkw=flash+drives&_fromfsb=0&_trksid=m270.l1313)

---

### Post by sloggerkhan on 2008-08-27
I'd use fdisk - based utilities for formatting. I have not had good luck formatting flash from gparted.

---

### Post by moshuptrail on 2008-08-27
I formated the drive (using gparted) into 4 2Gb partitions.  Only the 1st one works.  The others appear to format, but gparted does not recognize them after re-scanning.  This sounds like the behavior of a counterfeit drive.
BUT, I need still need to recheck with Windows which seemed to work.
Also, what is the fdisk related format command in Ubuntu?  (I'd like to try formatting that way too)

---

### Post by sloggerkhan on 2008-08-28
The 3 commands you need to look into details of are probably:
 mkfs.vfat -n <name> /dev/<device>
 fdisk -l
 fdisk /dev/<device>

you can look up the procedure elsewhere (including these forums) but generally, you use fdisk on a device, clear the whole thing, make a new dos partition table, make a new primary partition, set the disk label to the format you want to use, then run the mkfs.<format> -n command to name it and do the final format.

---

### Post by RedPandaFox on 2008-08-28
Its not going to work under any circumstance.

You bought it off eBay.
Big mistake.

I bought an 8GB USB and an 8GB SD card off 2 different sellers.

The 8GB was a 2GB compressed so many times to look like an 8GB and the SD Card had been recoded or something to look like an 8GB. If you bought it very recently raise a complaint on eBay.

---

### Post by moshuptrail on 2008-08-31
After  working with this flash drive extensively, I am convinced it will work as a 2Gb drive.  Just have to format the first partition as 2Gb and then leave the rest of the drive undefined.  I was able to determine that Windows appeared to work past 2Gb, but actually opening files located above the 2Gb line showed them to be empty or corrupt.

Not a Ubuntu problem at all.

Have a SNAD report with PayPal to get a refund.

---

### Post by benjaminbarch on 2009-06-01
Similar problem here. I bought an 8gb drive off of eBay (item# 180356422577) and have a problem with anything above 2Gb. Anything above 2Gb becomes corrupted and read only under ubuntu 8.10 but works fine under Windows XP. The drive is also VERY slow, making me believe it is doing some sort of on-the-fly compression while writing to the drive.

Mine is probably a 2Gb drive made to look like an 8Gb as well. I'll be getting my money back.

---

