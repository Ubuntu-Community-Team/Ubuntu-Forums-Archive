---
title: "Install won't run, just get black screen"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by gamesandguns on 2009-04-30
I have been struggling with Ubuntu 9 for a couple days now.  When I boot from the disc, it comes up to the main Ubuntu screen where it offers the option to try Ubuntu, install, check disc, etc.  If I select either to "Try Ubuntu without changing my computer" or the install option, the CD drives spins up and after 30 seconds or so, I get a black screen with nothing but a blinking cursor in the upper left corner of my screen.  I have left it over night and nothing happens beyond that point.  

Before I tried to install version 9, I had a dual-boot set up with version 8 and Windows XP Home.  Ran beautifully.  I tried to upgrade to version 9 and something happened that corrupted Ubuntu 8.

Troubleshooting I've done so far:
-Checked to make sure my laptop meets the minimum requirements - it does
-Redownloaded the image on a different computer than the first time and burned another install disc.  It works on other computers, just not my laptop.
-Deleted all partitions on hard drive.  Even removed hard drive.  Had no effect on problem

Laptop Specs:
Dell Inspiron 2650 - approx 6 years old
Intel Pentium 4 1.6GHz
384MB Memory
40GB Hard Drive
CDRW/DVD Combo drive

Anyone have any ideas?  Thanks!

---

### Post by taurus on 2009-04-30
At the initial screen (from Ubuntu LiveCD), pick F4 and use the safe graphics mode to boot/install Jaunty on your machine.

---

### Post by gamesandguns on 2009-05-01
I've tried that.  Same result as a normal install.

---

### Post by taurus on 2009-05-01
What graphic card does it have?  And if Intrepid (8.10) runs fine on that machine but not Jaunty, then stick with Intrepid (or even Hardy since it's a LTS--Long Term Support).

---

### Post by owend on 2009-05-01
Have you checked the md5 sum? and which file did you download - you probably need Ubuntu-9.04-desktop-i386.iso? (Not ...amd64.iso)

---

### Post by Bucky Ball on 2009-05-01
One question; if your rig was working perfectly, why did you upgrade? 8.04 LTS (long term support) is supported for three years more or so. 9.04 was only recently released and is really still not quite cooked (even though released). There will be bugs about for awhile.

Rule of thumb? Download the ISO (torrent most reliable), burn disk, check the disk, put disk in a drawer for a fortnight to a month then install, get updates and hope they fix the bugs that were around when you downloaded the ISO!

And my other rule of thumb: if it ain't broke, don't fix it! (I need my machines to be stable most of the time but when the holidays come around, I remove the safety net and start breaking some things.) :)

---

### Post by gamesandguns on 2009-05-01
My laptop has a GeForce 2 video card in it.  16MB video mem, I think.  
 
I wanted to upgrade to keep up with the latest version of Ubuntu.  I did make sure that I had the x86 version and not the x64 version.  I know it's not an issue of a corrupt disc because I've downloaded it at work and at home, burned a disc from each place, and it does the exact same thing.  We're using another disc burned from the same image that I downloaded at work on another laptop and it works great.

---

### Post by nategood on 2009-05-01
i'm having the same problem.  burned the iso (i386) and get through the initial ubuntu icon loading screen and then i get either a blank screen or screen with blinking cursor (in safe graphics mode).

System:
Intel Pentium 4 3.2GHz HT
2GB RAM
Master HD: 200GB IDE
Slave HD: 80GB IDE

I had 8.04 working.  I know i'll hear not broken, don't fix it... but i was having problems with my usb devices (non worked).  Figured I'd give the upgrade a shot from the ISO.

---

### Post by ronparent on 2009-05-01
From the live cd at the menu, try F6 to set no-apic no-lapic.

---

### Post by gamesandguns on 2009-05-01
I'll give it a try and let you know if it works.  Thanks!!

---

### Post by Bucky Ball on 2009-05-02
> **nategood said:**
> 

I had 8.04 working.  I know i'll hear not broken, don't fix it... but i was having problems with my usb devices (non worked).  Figured I'd give the upgrade a shot from the ISO.

It was broken and that was one way of trying to fix it, then. That&#347; different. :)

---

### Post by gamesandguns on 2009-05-04
I figured out the problem.  At the CD boot menu, I pressed F6 and chose the option that turns off ACPI.  System boots and works great now.
 
Thanks everyone for all the help!!!

---

### Post by Bucky Ball on 2009-05-05
Welcome. Good news.

---

