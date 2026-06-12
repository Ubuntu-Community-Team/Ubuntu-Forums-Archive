---
title: "xUbuntu Install on Lifebook B"
date: 2009-07-09
forum: Installation &amp; Upgrades
---

### Post by Phil_C on 2009-07-09
Hello All,

I have got xUbuntu to install on my very old lifebook B laptop (does not have bootable USB, CD or Floppy) by performing the following.

You will need 2 hard drives (I will call them HD1&HD2) and an external HD caddy.
HD2 will be spare at the end of the process and HD1 will be you laptops Hard Drive.
Both hard disks need to be partitioned (as you see fit).

Install xubuntu install files onto HD2 using the caddy and a separate computer.

Put HD2 into the Lifebook and HD1 into the caddy and connect to the lifebook.

Power on; this should boot to the install loader. 

Step through the installation process and select to install to the partition on HD1 (in the caddy). 

Once the installation is complete. 
Swap out HD2 and HD1, so HD1 is in the Lifebook.

You should now have a workable installation of xUbuntu on your Lifebook.

I tried many other installation methods, but because it does not have a bootable CD, USB or Floppy this was the only method I could get to work.

Hope this helps
Phil

---

### Post by joshuajon on 2011-03-17
I've got a lifebook p1120 with no external drives as well.  The bios won't boot from USB hdd or cd by default.  

The strategy I employ to get linux on here is to install plop bootmanager [http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html) from a USB floppy.  This enables USB booting.  After that you can boot darn near anything off a Unetbootin USB stick.  Goodstuff!

#! has been the best so far... I can't get in to puppy for some reason.  I liked the idea of easypeasy but it's too resource intensive.  I'm about to give xubuntu a try!  Cheers!

---

### Post by joshuajon on 2011-03-17
spoke too soon. xubuntu seems to detect networking hardware but neither dhcp nor manual config works.

---

