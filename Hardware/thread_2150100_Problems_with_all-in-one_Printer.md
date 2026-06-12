---
title: "Problems with all-in-one Printer"
date: 2013-05-30
forum: Hardware
---

### Post by Foskito on 2013-05-30
So I was working with ubuntu 12.04 until last weekend, and everything was going well in there, but I decided to move to 13.04 because my computer nedded a good formating. The problem is that after the change of version my printer is giving me trouble. 
I have a HP Deskjet 3050A wireless all-i-one and when I installed it directly from Settings> printer it gave me no problem it recognized it and printed without a problem, but there was no way of making the scan option to work (doesn't even show as a scanner option), so I decided to try installing with HPLIP guessing that it would give me less problems and that was a total mistake. Now the device appears as a scanner option but it doesn't scan, neither prints anymore only says there is a communication problem with the printer. I tried to fiz this but to be honest it seems it goes beyond my level of knowledge. How can I make it to work as a printer and a scanner again? any insights?

---

### Post by cforput on 2013-06-03
Well, I was on 11.10 and both printing and scanning worked beautifully. Then I upgraded to 13.04 (12.04 first, then 12.10, then 13.04) and now I can't even print. Thanks Ubuntu.

What I did to get my scanner to work was:


 1. Get new IP address from printer display
 2. Open browser
 3. Enter IP address from #1 in URL
 4. HP Printer utility will open
 5. Setting up the Scanner
     a) Click on Settings
     b) Log in as Administrator
        There was no password for my config
     c) Click on Security
     d) Click on Administrator settings
     e) Enable Webscan by placing a check in the box
     f) Click the Apply button

Good luck. The one thing I've learned over the years working with Ubuntu is that what works for one doesn't always work for all. I'm not Ubuntu expert by any means so if this doesn't work, I double I would be able to help. Hopefully it does.

---

### Post by Mark Phelps on 2013-06-04
Don't have an immediate solution -- but what I would advise to prevent this problem in the future is to BEFORE you do an upgrade, install Clonezilla and image off your current WORKING setup to an external drive.  That way, when upgrades go badly (and they often do, in my experience) you have a way to restore the WORKING setup in only a few minutes.  Unfortunately, even after all these years, Canonical still has NOT seen fit to provide any kind of "roll back" capability to back out version upgrades.  So, if things don't work, you're stuck fixing them or having to reinstall from scratch.

---

### Post by cforput on 2013-06-04
> **Mark Phelps said:**
> Don't have an immediate solution -- but what I would advise to prevent this problem in the future is to BEFORE you do an upgrade, install Clonezilla and image off your current WORKING setup to an external drive.  That way, when upgrades go badly (and they often do, in my experience) you have a way to restore the WORKING setup in only a few minutes.  Unfortunately, even after all these years, Canonical still has NOT seen fit to provide any kind of "roll back" capability to back out version upgrades.  So, if things don't work, you're stuck fixing them or having to reinstall from scratch.

Clonezilla would probably be a great thing to have regardless. I'll look into it. The issue I have is that the last version that worked with any consistency is 11.10 which is no longer supported so I would miss any updates and security patches, etc.

---

### Post by Mark Phelps on 2013-06-04
The other issue that tends to "get" folks who just do upgrades routinely and hope for the best is that of restricted video drivers.

For example, if you have one of the AMD HD 2x/3x/4x series video cards, have installed the AMD restricted drivers, are running 12.04.1 -- and routinely just upgrade to 13.04, you will lose your video!  Why? Because 13.04 contains a new version of the X-server that is incompatible with those drivers.  So, how easy do you think it will then be for folks to "fix" that when they don't even get working video?

Which is why, it is always a good reason BEFORE a version upgrade to do an image backup using Clonezilla.  A few minutes of backup can save hours of frustration when an upgrade goes badly and you don't even have a working desktop.

---

