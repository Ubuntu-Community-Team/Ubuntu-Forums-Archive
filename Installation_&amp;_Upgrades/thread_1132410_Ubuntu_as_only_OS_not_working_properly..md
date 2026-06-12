---
title: "Ubuntu as only OS not working properly."
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by Zaydene on 2009-04-21
I had Vista on my computer, and It all of a sudden stopped booting, but I really like Ubuntu so I was planning on keeping it. Because (from what I understand) there is nothing on my hard drive.

When I try to use the live cd to install Ubuntu, I get a message that my partitions are to small and I need to free up like 200.....bytes, which was like 2gigs. I don't know what to do, I made a new partition from the 180g of unallocated space and it still says the same thing. Even when I try just press continue, ignoring the message, about 75% through installation, it says that my partitions weren't big enough.

[http://yfrog.com/bescreenshotjlsp](http://yfrog.com/bescreenshotjlsp) 
^gparted screenshot

---

### Post by Zaydene on 2009-04-22
Still requesting help.

"bump"

---

### Post by caveman59330 on 2009-04-22
what filesystem are formating it under.probably shouldn't matter but for Ubuntu I usually use Reiserfs Journaling. I was installing Mandriva Linux and encountered problems when I tried using anything but Ext3

---

### Post by wpshooter on 2009-04-22
If there is NOTHING on your hard drive that you need to keep/save, then why don't you just get [www.killdisk.com](www.killdisk.com) and WIPE the drive completely clean and then try the installation of Ubuntu.  I bet it will work then.  I would use the MANUAL partitioning method.

---

### Post by cariboo on 2009-04-22
My installation takes up about 4Gb of hard drive space for / . I have a seperate partition  for /home. I usually set up / as a 5-10 Gb partiton, just to be sure i have enough space to install all the extra programs I use.

---

### Post by Zaydene on 2009-04-22
wpshooter; So do I need just get the free version of it? Because there isn't any OS I can't download a program. So would I need use killdisk's cd booter?

---

### Post by wpshooter on 2009-04-22
> **Zaydene said:**
> wpshooter; So do I need just get the free version of it? Because there isn't any OS I can't download a program. So would I need use killdisk's cd booter?

I believe that there is both a diskette version and a CD version.  Personally, I use the bootable CD version.  Yes, you would need to have a working computer to do the download and creation of bootable version of killdisk.

---

### Post by snowpine on 2009-04-22
> **Zaydene said:**
> I had Vista on my computer, and It all of a sudden stopped booting, but I really like Ubuntu so I was planning on keeping it. Because (from what I understand) there is nothing on my hard drive.

When I try to use the live cd to install Ubuntu, I get a message that my partitions are to small and I need to free up like 200.....bytes, which was like 2gigs. I don't know what to do, I made a new partition from the 180g of unallocated space and it still says the same thing. Even when I try just press continue, ignoring the message, about 75% through installation, it says that my partitions weren't big enough.

[http://yfrog.com/bescreenshotjlsp](http://yfrog.com/bescreenshotjlsp) 
^gparted screenshot

This is much easier than some of the responses would suggest. :)
Run the Ubuntu installer. When you get to the Partitioning step, choose "Guided Install: Entire Disk." Post any error messages here, but I predict you won't have any.

---

