---
title: "Need help recovering corrupted and deleted files from an external hard drive"
date: 2009-11-08
forum: Hardware
---

### Post by dz3 on 2009-11-08
Hello, I am not sure if this is the correct place to post this, so if anyone knows where it should be placed, that would be great.

This is what happened: I have a 1Tb external usb hard drive that I was using to temporarily store some very important files. When I first recieved it, I partitioned it into four partitions. Two of those were EXT3, one 20Gb, and one 30Gb. The other two were FAT32, one ~823Gb and the other ~50Gb. I placed the important files in the 823Gb partition, and kept them there for a while. This was the only copy of these important files, anywhere (stupid, I know). I made the two EXT3 partitions so that I could later install operating systems on them, but instead of booting with an installer CD, I thought it would be faster to use the "USB Startup Disk Creator" that Ubuntu provides. I opened it, selected an image I wanted, and selected the partition I wanted to load it into. It then said that it needed to be formatted, and I figured that it was alright, because it would only change the filesystem, considering it even showed up as different drives in the utility. When it did this, USB startup disk creator locked up for a bit. When I looked at my drive, I could see the indicator light flashing, so I knew that something was being transfered. I immediately thought that it may be formatting my entire drive. Then I made the huge mistake of pulling out the usb cable from the computer. I then put it back in the computer, and sure enough, it had removed all my partitions and left with a single 1Tb partition, with 310mb of of data in it. All the files were scrambled, and I could not copy the files to my computer's hard drive. Originally, there was at least 50gigs of data, but now only 310mb left, and they were all corrupt. It reads the new filesystem as msdos, but the original partition was FAT32. Is there any way that I can recover any of these files? Do you think that I should delete the remaining files, and try to recover them all at once?

---

### Post by phersotty on 2009-11-08
Wow, I'm sorry.... hopefully you can recover your files.  I don't have a lot of forensic experience, but you might try something like [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)  or this [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

I would recommend using a live system to access your drive so that no more files are written to it.   

I've used those tools for setting up hard drives for new installations and resizing existing partitions, but have no experience in recovering lost data.

---

### Post by dz3 on 2009-11-08
Thank you for the quick reply, phersotty. I checked those tools, and I think that I should be safe by running it from an installed operating system, as I have unmounted it so that no data can be written to it.

---

