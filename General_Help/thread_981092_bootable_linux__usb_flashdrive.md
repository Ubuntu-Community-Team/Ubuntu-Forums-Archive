---
title: "bootable linux  usb flashdrive"
date: 2008-11-13
forum: General Help
---

### Post by t3chn0n3rd on 2008-11-13
anyone running linux on a portable usb drive?

---

### Post by Steve1961 on 2008-11-13
yep, running Intrepid on a USB stick at the moment.  I'll eventually install it on my eeepc (it has Hardy on at the moment), but I like to wait around 6 weeks after a release just to get the first batch of updates through.

It's relatively easy to create a linux pendrive these days with [unetbootin]("http://unetbootin.sourceforge.net/") and Intrepid even has an option to create a usb drive built into the menus

---

### Post by C.S.Cameron on 2008-11-13
Have it running on a USB hard drive and several pendrives.
There are several ways to do it.
Disk image of the Live CD, disk image with persistence and Full install.
The persistent install of 8.10 using usb-creator does almost everything a full install does now.
I just got XP working inside Virtual Box on a 4 GB flash drive.

---

### Post by t3chn0n3rd on 2008-11-20
thanks for the replies.

---

### Post by PGTips91 on 2008-11-25
I recently did a full install of an Xubuntu derivative to my 4 GB Rundisk USB flashdrive. I managed to boot it from a specially prepared booting CD and then it was  booting directly from power-on and working as a normal HDD installation for a couple of days. 

Then I found that MS Windows XP would no longer boot on that computer. After I got XP booting again the flashdrive no longer boots. I'm still learning how to set up a CD that will boot the flashdrive. I succeeded once, without knowing exactly how, so I know it is possible but can't yet repeat it.

Since then I have installed Puppylinux onto the same partition, in a non-destructive installation. I can boot from the CD, run with the entire system in RAM memory, and write the changes to the flashdrive when shutting down. This uses a minimal amount of memory and I have allocated 512 MB to the storage file. This seems to be the more robust method I've seen so far as not all computers support booting from USB device, but all support booting from CD. A credit-card sized CD would be sufficient to carry the bootable Puppylinux, I think, and the flashdrive will keep the persistent image and any other data files desired.

Some claim that there is a limit to the number of writes possible before the flashdrive fails, but the number is between 100,000 and 100,000,000 so I'm not too worried about it failing any time soon. However, for those who are, the Puppylinux installation only writes occasionally or on shut-down, so the life of the drive should be extended almost indefinitely.

Paul

---

