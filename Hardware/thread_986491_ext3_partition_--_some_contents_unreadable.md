---
title: "ext3 partition -- some contents unreadable"
date: 2008-11-18
forum: Hardware
---

### Post by le_vainqueur on 2008-11-18
I just reformatted a partition which was NTFS to ext3.  I opened the properties of the ext3 partition and it correctly identifies the total capacity as 51.8 GB, but it says that 2.8 GB is used.  I have not put any files onto this partition, however.  

In the "contents" portion of the window, it says there is 1 item with size 16.0 KB and it also says in parentheses (some contents unreadable). It is this latter part that I am concerned about.  Two questions:

1. Is this something to be concerned about (ie. is my hard drive failing)?

2. How can I recover this disk space?



Thanks for the help,

LV

---

### Post by taurus on 2008-11-18
51.8GB times .05 (5%) is 2.59GB.  Ext3 will reserve 5% of your disk for root.  You can set it to 0% if you want.

---

### Post by le_vainqueur on 2008-11-18
Thanks for the info.  I was not aware of that.  Why does it do this?  Is there a reason to have more/less reserved?  Also, should I be concerned about the fact that it says "some contents unreadable"?

---

### Post by taurus on 2008-11-18
The reason ext3 will reserve 5% of your disk space as a default in case you accidentally fill it up, you (or at least root) can still log in and remove some files, freeing up some space.  And if you don't have that space reserved, then you won't be to even log in when you run out of space.  In that case, you have to fix it from a LiveCD.

---

### Post by SunnyRabbiera on 2008-11-18
right, its there as a just in case method

---

### Post by le_vainqueur on 2008-11-20
> **taurus said:**
> The reason ext3 will reserve 5% of your disk space as a default in case you accidentally fill it up, you (or at least root) can still log in and remove some files, freeing up some space.  And if you don't have that space reserved, then you won't be to even log in when you run out of space.  In that case, you have to fix it from a LiveCD.

I see...that makes perfect sense.  I have had this happen to me in Windows before -- I filled up my hard drive and I couldn't even uninstall a program because there was no disk space available.  I'm glad to know I won't have to worry about that.  I assume that my partition with my Ubuntu installation on it has the same thing since it is ext3?

---

### Post by BobCFC on 2008-11-21
If this is a **data partition only** then you might as well recover the lost 5% which is just being wasted.  The 5% reserved is meant for the root partition and you can do the following to disable it for DATA DRIVES:


Open System&#8594;Administration&#8594;System Monitor and click on the File Systems tabs to see information about the currently used partitions.

Top of the list should be /  (root).   DO NOT TOUCH THIS.

Following this maybe several data partitions depending on how you have formatted your hard disks.  e.g.  I have a separate home partition, and a couple more for TV and MOVIES on different disks.  These are of no use to root so I am going to free the 5%.

Look at the columns FREE and AVAILABLE to see the difference between them.  (Only for Ext3 or 2 not NTFS etc)

Once you have chosen a partition make a note of it's DEVICE NAME.  In this example I will use  **/dev/sda2**  THIS WILL BE DIFFERENT ON YOUR SYSTEM.  Now open Applications&#8594;Accessories&#8594;Terminal and type the following command using YOUR DEVICE NAME INSTEAD.

```
 sudo tune2fs -m 0 /dev/sda2
```

It will say *Setting reserved blocks percentage to 0%* and a few seconds later you can see the free space update in System Monitor.  This could be 30gb+ depending on you disk sizes.

---

### Post by le_vainqueur on 2008-11-23
Thanks for the advice.  If it's not needed, I may as well have it for myself.

---

