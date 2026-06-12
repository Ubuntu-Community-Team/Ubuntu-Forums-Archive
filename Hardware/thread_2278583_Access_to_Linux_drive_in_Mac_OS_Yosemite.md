---
title: "Access to Linux drive in Mac OS Yosemite"
date: 2015-05-17
forum: Hardware
---

### Post by maincm on 2015-05-17
So, my girlfriend dropped my laptop. All seems to be fine, except the screen. Hello darkness, my old friend! Honestly, the laptop is too old to do anything but access the data I need and move on. I bought an external hard drive enclosure, and plugged it into the only other computer I have access to: a Macbook Pro with Yosemite. I am able to see the hard drive in Disk Utility, but I can't mount it or access anything. I tried using MacFUSE and Fuse-Ext2, but I couldn't get them to make it readable. I have a ton of school, work, and entertainment files on the hard drive that I would hate to lose. 

The hard drive is formerly Ubuntu, I think 14.10. It was my startup, and only, drive in the now dead laptop. Does anyone have any bright ideas on how to gain access to the data?

Thank you so much to any and all who can help!

---

### Post by weatherman2 on 2015-05-17
Boot a live USB Ubuntu on the Mac.  Then you should be able to see you data on the drive in the enclosure.  But then - what will you copy it to?  I think Ubuntu can't write to Mac partitions by default but can read the, and that won't help you.  If you have a Windows-format portable drive, though, you'd be able to copy using the Ubuntu live boot from your old drive to a Windows partition, and Mac should be able to see that.

---

### Post by maincm on 2015-05-17
I thought the same thing, weatherman. Just boot camp Ubuntu onto the Macbook. Like you said though...once that's done, copy it where? A separate external hard drive that is viewable/editable by both Ubuntu and Mac? And what would that be? From your post, I gather a Windows-formatted external may work. 

What do you think? Anyone else?

---

### Post by Vladlenin5000 on 2015-05-17
> **maincm said:**
> I gather a Windows-formatted external may work.

Indeed, it should work. Just make sure it's NTFS if you intend to save files larger than 4GB, the file size limit for FAT32.

---

