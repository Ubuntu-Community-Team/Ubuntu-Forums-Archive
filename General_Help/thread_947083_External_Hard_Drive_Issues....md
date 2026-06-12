---
title: "External Hard Drive Issues..."
date: 2008-10-13
forum: General Help
---

### Post by Prominence on 2008-10-13
Do the issues ever stop? That's all I have to ask but...here's all you have to go on: 

[http://lh5.ggpht.com/Graysonisdaman/SPQQYED08zI/AAAAAAAAAc8/C-CowjQxq_w/Screenshot-gnome-mount.jpg](http://lh5.ggpht.com/Graysonisdaman/SPQQYED08zI/AAAAAAAAAc8/C-CowjQxq_w/Screenshot-gnome-mount.jpg)

---

### Post by Washer on 2008-10-14
the hard drive is using NTFS. You must not have "safely removed" it from within windows. Just boot back into windows & check it for errors, i forget the exact terminology. Right click on the drive, go to properties, & search for something about scanning it for errors.

My advice is to reformat to EXT3 if you don't plan to use it *at all* on windows, or FAT if it's < 4gb.

---

### Post by Prominence on 2008-10-14
Thank you! Still kinda find it a shame that windows is still nessecary...

---

### Post by bigbrovar on 2008-10-14
> Prominence  	
Re: External Hard Drive Issues...
Thank you! Still kinda find it a shame that windows is still nessecary... 
nat 
NTFS is a proprietary Microsoft technology and the driver for it was not released for linux. it was made to work on linux using reverse technology but even then u have to properly remove it from a windows system or it wont automount on linux. unless uwnat to forcefully mount it. something u can do on ubuntu without using a windows system .. if u want ot be completely free of windows how about first free your self of windows techology

---

### Post by bob200800 on 2008-10-14
A USB flash drive consists of a NAND-type flash memory data storage device integrated with a USB (universal serial bus) interface. USB flash drives are typically removable and rewritable, much shorter than a floppy disk (1 to 4 inches or 2.5 to 10 cm), and weigh less than 2 ounces (56 g). Storage capacities typically range from 64 MB to 64 GB[1] with steady improvements in size and price per gigabyte. 
_________________________________________________________________________
[Carhartt Jeans](http://www.workwear1.com/browse.cfm/2,83.html) [dubai real estate](http://www.choicepropertyinvestment.com/international-developments/dubai-property-investment/)

---

### Post by Prominence on 2008-10-15
point taken

---

### Post by jerome1232 on 2008-10-15
If the problem was just the 'unclean log' then the program ntfsfix can help you out. If you install ntfsprogs it gives you a suite of tools to work with ntfs.

```
sudo apt-get install ntfsprogs
```

I think the point has been made but that's like complaining that Windows can't mount a disk formated as jfs, or xfs, or reiserfs. ext2/3 is in luck because there's a third party driver for windows that lets it use ext2 (ext3 is backwards compatible with ext2)

---

