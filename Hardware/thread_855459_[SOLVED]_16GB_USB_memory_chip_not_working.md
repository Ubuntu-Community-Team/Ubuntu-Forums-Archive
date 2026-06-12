---
title: "[SOLVED] 16GB USB memory chip not working"
date: 2008-07-10
forum: Hardware
---

### Post by iheartubuntu on 2008-07-10
I have an 8GB chip from [http://www.adata.com.tw](http://www.adata.com.tw) that works great on my Ubuntu 8.04, and my sister bought an identical looking USB chip, but 16GB and it doesnt work with any linux system.

Is there anything I can download to get this to work for her?

Here is a similar looking product by the same company (although ours is diff color)...

[http://www.adata-group.com/en/product_show.php?ProductNo=AP01ZZZSV](http://www.adata-group.com/en/product_show.php?ProductNo=AP01ZZZSV)

...and it says it works fine with linux kernel 2.4 or later and Im running 2.6.24-19 Its not working :|

Any help would be appreciated, thanks!

---

### Post by iheartubuntu on 2008-07-10
* bumpity bump *

---

### Post by ljonesj on 2008-07-10
it could be its format if its formated to ntfs it might not read u may need the driver to get to read or go to a windows machine and format it to fat 32 or 16 to see if that workes sorry i cant be more usefull in that department

---

### Post by llama320 on 2008-07-10
+1 to the ntfs thing. Go into a windows box and see what the format of the disk is.

If there's no luck after formatting it to vfat you can try booting into ubuntu, plugging in the drive, then pasting the output of dmesg here

Good Luck

---

### Post by silkstone on 2008-07-10
Does anything happen when you plug it in?

Look in /var/log/kern.log

That should record whenever a USB device is inserted. If it is being recognised but not mounted, it may be that the filesystem is corrupt. If you have gparted installed, see what it makes of the USB stick.

AFAIK Hardy should recognise NTFS partitions without having to install anything else, but maybe there's an issue with USB flash drives. Most of these are formatted FAT32, although perhaps this larger one is NTFS.

---

### Post by ljonesj on 2008-07-10
i know this does not pertain to his problem but my 500 gig seagate free agent harddrive is ntfs from the factory so maybe his could be ntfs but who knows what his problem is without the dsmeg

---

### Post by iheartubuntu on 2008-07-10
I plugged it in again and used gparted and it found it.

Disk Label: MSDOS
File: Fat32

My sister might want to use this at her house which is still an XP setup. Which is the best to format this to? FAT32 again? or FAT16? NTFS isnt an option.

EXT3 would work if she was only using linux systems, right?

---

### Post by silkstone on 2008-07-10
OK - if gparted found it, the drive is there but it isn't being mounted. Not sure why - I'm no expert on these things. :)

There should be no reason to reformat it - FAT32 is OK for both Windows and Linux (though not ideal for either).

If you click on Places > Home Folder, is the drive listed in the sidebar down the left hand side? If so, you should be able to mount it by clicking on it - you may be asked for your password.

Try that and let's hope someone with more knowledge comes along to explain why it isn't happening automatically!

---

### Post by iheartubuntu on 2008-07-10
I did an experiment of partitioning the drive as 8gb FAT 32 and 8gb EXT3. Theoretically, on an XP system it would show only 8gb, correct?

After I did this, I plugged the chip back in and in Ubuntu up came two drives, one was 8gb and the other was 8gb :) so there must have been a problem with the format as to why the drive wasnt being loaded up.

I then decided, what the heck - lets format the entire drive as FAT32 again, and sure enough I can read it fine as a 16gb chip now.

THANKS for the tips to get me going here :)

---

### Post by silkstone on 2008-07-10
Great! I was a bit puzzled about the drive name - 'MSDOS' - and I was going to suggest reformatting it (as FAT32) because it sounded as if the initial formatting might be corrupt or it would have a better label.

---

