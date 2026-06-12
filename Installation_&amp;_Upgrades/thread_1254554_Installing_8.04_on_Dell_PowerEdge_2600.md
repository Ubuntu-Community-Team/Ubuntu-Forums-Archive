---
title: "Installing 8.04 on Dell PowerEdge 2600"
date: 2009-08-31
forum: Installation &amp; Upgrades
---

### Post by b89.smith on 2009-08-31
I have a Dell PowerEdge 2600 with 2x 2.4 GHz Xeon processors and 2GB of Ram. When the server boots up I have it set to boot first from the DVD drive. When the 8.04(x86) desktop install disc boots it comes to the screen showing the ubuntu logo with options to try ubuntu as a live cd, to install it and several other options below. When I select either the live cd or install option the dvd drive shows activity for 30 or so seconds then it stops reading and the server stays at that screen. I left the server and came back an hour later, it still showed the ubuntu logo with the install options. Am I installing the wrong edition of ubuntu? What would you recommend to do to fix this problem?

---

### Post by earthpigg on 2009-08-31
burn to a CD-R, and burn at the slowest speed possible.

if that doesn't work, re-download the .iso file - and download it via torrent.

if you are short on CD-Rs, download the .iso via torrent and then burn at slowest speed possible. 

this is all intended to minimize the chances of a single one or zero in the wrong place, which can kill an operating system install quite effectively:

-CD-Rs burned at slowest speed are the most reliable. i know DVD-R or RW and whatnot are the wave of the future, but they do not serve our purposes as well or as reliably as a good old fashioned CD-R will.
-torrents do error checking on-the-fly as they download.
-check here to ensure you aren't making any common mistakes: [https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)

---

### Post by jerrrys on 2009-08-31
if CD is not an option for you and you can boot from USB

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by b89.smith on 2009-08-31
Do I need to change a setting in my bios to boot from a usb drive or will it automatically reconise it as a bootable drive?

---

### Post by jerrrys on 2009-08-31
I don't know if your Dell will do that or not.  Just try and if not, do it in BIOS.

---

### Post by xX_Q_Xx on 2010-04-19
I had the same problem. Tried it on a couple different machines. I ended up re-burning the live CD and it finally worked. However, now I am running into an issue where my Ubuntu (9.10 Desktop edition) does not recognize a partition which consists of 6 drives in RAID 5. 

It is installed on a partition (2 drives in RAID 1) on a Dell Poweredge 2600 and there is a RAID card managing the hardware RAID. The same RAID card also manages the other 6 drives in RAID 5. Ubuntu boots fine, but it does not see the 2nd partition.

From what I have been reading, Ubuntu doesn't work well with hardware RAIDs. Is this accurate? Is there a work around for this? Can someone please point me to some documentation which may help me with this? Thanks a bunch!

~Q~

---

