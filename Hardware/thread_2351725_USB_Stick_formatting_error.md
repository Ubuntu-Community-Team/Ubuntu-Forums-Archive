---
title: "USB Stick formatting error"
date: 2017-02-06
forum: Hardware
---

### Post by linusheinz on 2017-02-06
Hey ,
I tried to make a bootable USB under Windows with Rufus and I got a formatting error. Then I tried to format it with Windows and cmd, it didn't work. Now I'm in ubuntu, and the USB didn't show up after plugging it in but it was displayed in the Disk's utility: [Screenshot]("http://i.imgur.com/CHjHTf5.png"). Neither the command sudo fdisk -l  nor gparted show it.

---

### Post by TheFu on 2017-02-06
Welcome to the forums.

Don't know the answer. A few ideas below.

Sometimes USB disks aren't compatible with every USB controller.  Try a different port on the opposite side of the computer. It might use a different controller.  I've seen a few cheap and a few expensive flash drives refuse to work on some of my computers, but not all. I've never found a pattern, just that some flash drives don't work with computer Z, but do work with computer A.  A few of my sticks work with all of the computers, but cannot be used to boot from 20% of them.  If this flash drive ever worked with this computer, then compatibility likely is NOT the issue.

Sometimes USB disks wear out. There are a limited number of writes that any flash storage device can support. Cheaper flash drives don't have wear leveling, so the same parts of the storage get written over and over and over.  I've had a few go bad after about 4 yrs of use.

I've never used rufus, but hear good things about it.  Been using "**yumi**" here on Windows and **dd** on Linux to make bootable media.

I'd use **dd** to zero out the first few sectors, then remove and reset the USB device and create a new partition table on it.  If possible.

Those are my only guesses.  Probably won't help., but might.

---

### Post by linusheinz on 2017-02-06
Thanks for the response i tried dd The result :[ dd]("http://imgur.com/a/vlxJh")  but if i try to create a new [COLOR=#000000] partition table   with fdisk it says the drive is write protected :([/COLOR]

---

