---
title: "LiveUSB Creator - Boot Error!"
date: 2009-10-20
forum: Installation &amp; Upgrades
---

### Post by Davey_S on 2009-10-20
Hello,
 
I am fairly new to Ubuntu, and have been using a live cd version of it for a few weeks now (the problem is my hard drive, it needs replaced so that is why I am working off a live cd). I would ideally like to run this off USB so I can have my cd/dvd drive free.
 
So, using a brand new 4GB Kingston DataTraveller, I opened up the liveUSB Creator, and without any problems, my live USB was created. Or so I thought..
 
I restarted the computer, putting "USB Memory" to the top of BIOS, and it tried to boot, but failed. It now says "Boot Error."
 
So, I am back to square one, using the live cd. Any suggestions of what I can try to do now? Was there something I should have done before using the liveUSB creator, for example did I need to partition my USB??
 
Any help would be much appreciated.
Davey_S

---

### Post by Mighty_Joe on 2009-10-20
I've run into several problems with the USB Creator (see my post in [this topic]("http://ubuntuforums.org/showthread.php?t=1242539")).  What other BIOS options do you have?  I've seen the wrong choice cause [lots of problems]("http://ubuntuforums.org/showthread.php?t=1266014")

---

### Post by presence1960 on 2009-10-20
My BIOS recognizes flash drives 4 GB or higher under Hard Disk in BIOS. When I boot from a 4 GB or larger flash drive I go into BIOS and under hard disk boot order move the flash drive to #1 position.

It could also be it was created incorrectly. You can try using unetbootin to create a bootable flash disk. It is in the repositories or you can get it [here]("http://unetbootin.sourceforge.net/").

---

