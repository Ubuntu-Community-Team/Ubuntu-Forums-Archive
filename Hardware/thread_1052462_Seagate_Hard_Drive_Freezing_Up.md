---
title: "Seagate Hard Drive Freezing Up"
date: 2009-01-27
forum: Hardware
---

### Post by lariosa42 on 2009-01-27
Dear Ubuntu Forums,

Would you help me figure this one out?  I have a 750GB Seagate "FreeAgent" external USB drive which has worked more or less well until recently.  After unplugging the thing while I was on vacation for a month, I hooked it up again to transfer some data from my laptop.  It starts copying files, but after a minute or so, the copy progress bar just stops.  I can't close the window and I have to force-quit.  I try it again, and get the same results.  As a shot in the dark, I try [this]("http://ubuntuforums.org/showthread.php?t=494673") post, but get the same result again.

My laptop's hard drive is nearly full, and needs to be relieved.  Any help?  Thanks in advance!

---

### Post by 2hot6ft2 on 2009-01-27
Might want to check this out.
> **cob said:**
> Uh, it's not a Seagate drive, is it?

[http://news.cnet.com/8301-17938_105-10146909-1.html](http://news.cnet.com/8301-17938_105-10146909-1.html)

---

### Post by lariosa42 on 2009-01-28
Thanks, but as I mentioned, my drive is the "FreeAgent" model, not the Barracuda nor the DiamondMax.  Also, my problem was not that my drive was unrecognized, but that it freezes up.  Therefore, the bug fix in the article will not help my problem.  Thanks anyway.

---

### Post by AKADAP on 2009-01-28
Free agent is an external drive that may contain a barracuda internally. Go to the Seagate website and check to see if there is an update. 
They will probably also have tools you can use to test the drive to see if it is working properly.

---

### Post by lariosa42 on 2009-01-29
Thanks for the tip.  Unfortunately (or maybe, fortunately?) Seagate lists my drive as "unaffected" by any known bugs.  

Indeed, my problems seem different than the recent bug people have been talking about associated with the Barracuda drives.  I can read and files off of it with no problems.  I just cannot write to the drive, getting "Operation not supported errors."  This started happening after about 6 months of pain-free use.

---

### Post by gib2800 on 2009-02-12
I have the same problem with a Seagate Freeagent 750 gig I use with my Toshiba laptop dual booting Ubuntu Intrepid and winxp. It won't let me copy files to the external hard drive but will freeze up and give me an error saying something like "input/output error". It also has trouble reading files after a while of use. In winxp it does the same and will not let me "safely remove"; it says something like "cannot remove. drive in use. try again later". The Seagate program for winxp says upon testing the drive that it needs to be serviced. I have read a lot of bad reviews about Seagate lately and it looks like my drive needs to be replaced, I've had it less than 3 months. I'm still hoping it may be repairable.

---

### Post by gomson on 2009-02-12
> **lariosa42 said:**
> Dear Ubuntu Forums,

Would you help me figure this one out?  I have a 750GB Seagate "FreeAgent" external USB drive which has worked more or less well until recently.  After unplugging the thing while I was on vacation for a month, I hooked it up again to transfer some data from my laptop.  It starts copying files, but after a minute or so, the copy progress bar just stops.  I can't close the window and I have to force-quit.  I try it again, and get the same results.  As a shot in the dark, I try [this]("http://ubuntuforums.org/showthread.php?t=494673") post, but get the same result again.

My laptop's hard drive is nearly full, and needs to be relieved.  Any help?  Thanks in advance!
I think I might get flamed for this but I've noticed my external hard disks (be it new or not) having a rather short lifespan under ubuntu (linuxmint to be exact) usage. I've already lost 4 500GB hard disks since I stated using ubuntu, that's ins a space of 7 months. 2 of them were new disks.

It all starts with a wierd random clicking noise from the disks, then it get's worse and louder. 
I've had to go back to windows and I haven't had any problems since then.

This is a serious shot in the dark but could ubuntu be somehow shortening hard disk lifespan. I know there was a problem like this before relating to ubuntu and laptop hard disks, is there a possibility of the same thing going on (un-confirmed) with desktops as well....?

Remember, this is just an open discussion so please don't kill me :)

---

### Post by lariosa42 on 2009-02-18
Thanks for the input gib2800.  My hard drive is only a few months old too, and I spend around $150 for it, so I'm not too happy that it seems to be broken.  At least I can still read files off it (I just can't write to it).

gomson-
I remember there was a potential problem recently with some version of Linux killing harddrives.  I think it was fixed not too long after it was reported.  You might try a few searches and see what you can find.  In the mean time, you could try updating to the latest version of your distribution and see if that fixes it.

As for me, I don't know what I'm going to do.  Nobody seems to have a solution to this, my internal hard drive is essentially full, and I can't afford another hard drive right now.

---

### Post by handy on 2009-02-19
There have been a spate if bad Seagate HDD's over a period months.

Some of the problems Seagate have publicly acknowledged others exist that they have not admitted to yet.

I expect the OP needs a RMA & warranty repair.  If the problem is due to bad firmware, which has been very common, the data on the drive will very likely be safe.

---

### Post by lariosa42 on 2009-02-21
handy-

Thank you!  Finally, something I can work on to try to fix this.

Now, I just need to figure out what OP and RMA are, and how to repair the RMA & warranty...

---

### Post by gib2800 on 2009-02-21
I still haven't found a fix for this problem in Ubuntu Intrepid kernel 2.6.27-11.27 but have found some potentially useful information which seemed to temporarily fix it in older distros. Here's the link:

[http://ubuntuforums.org/showthread.php?t=494673](http://ubuntuforums.org/showthread.php?t=494673) 

It looks like the problem is a result of usb harddrives being mounted at multiple locations (sdb1, sdd1, etc) meaning it is a USB issue and not faulty hardware. 

The solution for the above post is copied below but does not seem to work with newer distros such as Intrepid

Create a udev rule:
```
sudo gedit /etc/udev/rules.d/85-usb-hd-fix.rules
```
with the following in it:
```
BUS=="scsi",KERNEL=="sd?",SYSFS{vendor}=="Seagate",SYSFS{model}=="FreeAgentDesktop",RUN+="/usr/bin/usbhdfix %k"
```
then create a shell script to run when the harddrive is detected:
```
sudo gedit /usr/bin/usbhdfix
```
with the following:
```
#!/bin/bash
echo 1024 > /sys/block/$1/device/max_sectors
echo 1 > /sys/block/$1/device/scsi_disk:*/allow_restart
```
then make it executable:
```
sudo chmod 0755 /usr/bin/usbhdfix
```

This code did not work for me, but I believe it might if it were updated for use in Intrepid's kernel. Does anyone see anything in the above code that could be modified for use in Ubuntu Intrepid?

---

