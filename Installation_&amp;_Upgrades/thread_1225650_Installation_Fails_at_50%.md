---
title: "Installation Fails at 50%"
date: 2009-07-28
forum: Installation &amp; Upgrades
---

### Post by caddyjoe77 on 2009-07-28
Hello all, having an issue with installing Ubuntu.  I have had it on my machine before, but lost my hard drive.  I installed a new 300GB WD Velociraptor and have tried several different methods of installing ubunu.

When i try installing after bootup and select "install ubuntu now" instead of using the Install program after i am in the live CD the formatting fails at 5 percent every single time and locks up.  If i boot to the Live CD, use GParted and install, it fails at 50 percent like clockwork when it is trying to install some PERL library files.  

The error given in I/O, talks about my CD drive being too slow or perhaps i should burn the image at a slower speed.  I know it more than likely isnt my HDD as it is brand new. 

Here are the things i have done to rectify the situation:  1.) New Hard Drive, New SATA Cable.  2>) New HDD, New SATA Cable on different SATA port on MoBo. 3.) Burned CD at a lower speed.  

I am wondering if perhaps my DVD drive is too slow?  It is on IDE.  I have also tried going back to 8.04 which i have successfully installed before with the same brand/type of CD but that doesnt work either. 

I am normally pretty good at this, but it appears my PC has finally kicked my butt.  

Here is a general setup:  6GB RAM, 300 GB velociraptor, 2 320 GB Sata drives, Intel Core2 duo 6600, GeForce 7600 GT, Diamond soundcard.  Gigabyte MoBo

thanks for whatever help you may be able to provide.  Is there perhaps a way to write my installation log to a USB stick and see what is happening?

---

### Post by m-p{3} on 2009-07-28
I got a brand new PC 3 months ago, and I had some problems installing Ubuntu, like locking during the installation. After some testing, I found out that one of my RAM module (4x2048MB) was defective. When I isolated/removed the faulty RAM module, the installation went through. I RMA'd the RAM, and I should receive it back pretty soon.

And even if it is a brand new hard-drive, I would do a surface test to be 100% sure it is not a faulty HDD. The quality assurance department might have failed to catch that one. If that's the case, bring it back to the retailer and ask for a replacement.

---

### Post by hamstersquasher on 2009-07-28
see if there are any DMA options you can adjust in the BIOS.  I had a similar issue and fooling around with DMA settings enough helped for me.

---

### Post by caddyjoe77 on 2009-07-29
Thanks, tried the RAM swapping and i still get the same result unfortunately. 

DMA settings?  I dont see any in my BIOS....blahh!!

anyone else have some ideas?  

Going to swap DVD Rom Drives to see what happens.  Even tough i have 2 DVD Roms, i dont see the likelihood they are both bad.  If they both show up as bad, then i would think thats more of an IDE issue.  

anything else? Agree? Disagree?

---

### Post by TrakerJon on 2009-07-29
Looks like disk read issues, the CD drive may be going bad...assuming it's not bad memory.

---

### Post by kickwin on 2009-07-29
> **trakerjon said:**
> looks like disk read issues, the cd drive may be going bad...assuming it's not bad memory.

+1

---

### Post by caddyjoe77 on 2009-07-29
Thanks! 

i will install my new drive in a few days, and post what happened for the betterment of the forum.

---

