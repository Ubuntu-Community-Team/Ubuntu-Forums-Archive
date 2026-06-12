---
title: "Trying to install, CD will not run"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by scott_s_06 on 2009-11-05
I am on Windows 7 64, and I downloaded the "ubuntu-9.10-desktop-amd64.iso" and burned the disc image to a CD.  When I stick the CD back into my computer windows brings up Autorun, and I tell it to run the wubu.exe, but nothing ever happens.  I even went into My Computer and double clicked on my disc drive and it does nothing.  I also right clicked and opened the drive and found wubi.exe and it will not run either.  I tried run as admin and compatibility.  
What should I do?
Thanks!

---

### Post by werecatomega on 2009-11-05
well, the easiest way i think would be to partition your computer from windows 7 (look it up), insert the CD, Restart your computer, enter the BOIS and boot from Disk. the setup should be strait foward from there

---

### Post by scott_s_06 on 2009-11-05
Ok now I am having trouble making the partition.  I made one as you can see that I named Ubuntu, but I cannot figure out how to make it Unallocated like one of the guides said to make it that I read.  What should I do?

[http://s299.photobucket.com/albums/mm299/scott_s_06/?action=view&current=partition.png](http://s299.photobucket.com/albums/mm299/scott_s_06/?action=view&current=partition.png)

---

### Post by Bob63 on 2009-11-05
I believe you need to boot your PC from the CD.

---

### Post by scott_s_06 on 2009-11-05
I did boot from the CD, but when I try and install I got very confused with all of the partitioning options it gave me, and I dont think it would let me install it on the partition that I created in windows because it was not set to unallocated? 

 Should I just delete this partition that I made in windows and let Ubuntu create a new partition on the drive?  Will this erase the data that I currently have on that drive?

---

### Post by Bob63 on 2009-11-05
> **scott_s_06 said:**
> I did boot from the CD, but when I try and install I got very confused with all of the partitioning options it gave me, and I dont think it would let me install it on the partition that I created in windows because it was not set to unallocated? 

 Should I just delete this partition that I made in windows and let Ubuntu create a new partition on the drive?  Will this erase the data that I currently have on that drive?

I think that would be best. I believe we are discussing the partition which is ID'd as K: in the picture? Windows formatted it as a NTFS partition, so when you try to install Ubuntu, its partitioner thinks the partition is in use by Windows. Either delete it from within Windows [go to the same screen you have in the picture, right click on the K: (Ubuntu) partition, Delete should be an option in the shortcut menu] and try reinstalling Ubuntu (the Ubuntu partitioner should detect the free space then), or if you can tell which is the proper partition using the Linux notation, you can use the manual option to have the Ubuntu partitioner erase the NTFS partition, then set it up and format it as ext3 or ext4, whichever you prefer.

Setting up the partition won't erase the info on the drive, it will reset that segment of the partition table and reformat that partition to ext3 or ext4. Actually on automatic it should set up a small swap partition and a /(root) partition in the resulting free space. Manually you should do this yourself.

---

