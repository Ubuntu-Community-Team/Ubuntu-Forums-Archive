---
title: "ubuntu and IBM R50"
date: 2005-12-12
forum: Hardware &amp; Laptops
---

### Post by wasan on 2005-12-12
Hi everyone,

I must say that I'm quite new to linux. But after I've a try with ubuntu (running on CD-ROM) it's really impressive to me. So I've planned to install it into my IBM R50 laptop but I'm not sure that I will have a problems with hardware's drivers or not. So if anyone has some suggestions or experiences about IBM R50 and ubuntu please kindly inform me. Many thanks

P.S. my laptop specifications are as follows:
ThinkPad R50 1829-I2A [change] 
P M 1.4GHz, 256MB RAM, 30GB 4200rpm HDD, 14.1 XGA(1024x768) TFT LCD, 32MB ATI Radeon 7500, 24x24x24x/8x CD-RW/DVD, Intel 802.11b wireless(MPCI), Modem(CDC), 1Gb Ethernet(LOM), UltraNav, Secure Chip, IEEE 1394, 6 cell Li-Ion battery

---

### Post by mips on 2005-12-12
I dont think you will have a problem and if you do it should easily be sorted out via these forums.

---

### Post by GrumpyBob on 2005-12-12
Well, I have had absolutely no trouble with installing Breezy on my R52 (dual boot with WinXP).

All the hardware I've tried has worked.  (I have never used the modem).

Robert

---

### Post by jml on 2005-12-12
I agree, you should not have any problems.  I loaded 5.10 on a Thinkpad R40 with nearly identical specs (my unit has 512 meg RAM).  And a used R31 with less powerful specs.  Graphics worked, sound, network, even the built in wireless card was recognized.  (not configured, but recognized)  

The only thing to be aware of is the "Protected Space" IBM sets up on the hard drive.  On my R40, IBM stores a complete restore image in a hidden partition.  I don't know if the R50 uses one, however.  So if you are dual booting with WinXP, or if you do not have physical restore discs, this protected area is the only way to do a restore to original specifications if you trash your system.  So be very careful when you partition your hard drive to not delete this partition.  I vaguely remember that this partition is hidden and may not be visible from within a partioning application.  If qparted lists your hard drive as being about 3-5 gig smaller than spec, the missing space is probably the protected hard drive partition.  Your IBM documentation should list the specifics.  You might also be able to find out some info by doing a Google Search using the search terms: IBM Thinkpad R50, Protected partition and Linux.  That was how I found out about the partition on my Laptop.  Another good resource for installing Linux on your Thinkpad is the "Linux on Laptops" web site.  It lists howto's for installing Linux on virtually every brand of laptop out there.  I have found it very helpful.  Sorry to ramble on, but I hope that this helps.

Joe

---

### Post by wasan on 2005-12-13
Many thanks to you all. Now, I will have a try....

---

### Post by darius_underhill on 2005-12-13
I was able to install UBuntu on a R50e and everything worked like a charm.  Although I had to tweak the xorg.conf file to enable some features for the trackpoint pointing device.  But overall, IBM makes great linux friendly machines.

cHeers!

---

### Post by zork-1 on 2005-12-21
Grumpy -- would you mind adding configuration details for your R52, including the video adapter?  Thanks ..

Wayne

---

