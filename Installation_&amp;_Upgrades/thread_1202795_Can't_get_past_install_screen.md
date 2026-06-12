---
title: "Can't get past install screen"
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by axelbaxel on 2009-07-02
I've been trying to install Ubuntu 9.04 for 2 days now, And I managed to get to the screen where you select to Boot from LiveCD or to install, but when i select any of these options, I get to a black command prompt screen.

I have tried with Different CDs and DVDs, and different download locations and they all resulted in the same problem, so that can't be the cause.
If my computer specs could help, here they are (taken from X-Fire):

Manufacturer:	
MSI
Processor:	
AMD Athlon(tm) 64 X2 Dual Core Processor 4600+, MMX, 3DNow (2 CPUs), ~2.4GHz
Memory:	
2048MB RAM
Hard Drive:	
500 GB
Video Card:	
NVIDIA GeForce 8600 GT (2 of them, SLI)

---

### Post by axelbaxel on 2009-07-02
The same thing is happening with the alternate installer.

Also I have waited 10 minutes without it doing anything.

---

### Post by merlinus on 2009-07-02
Did you checksum your .iso, and burn at no more than 4x?

---

### Post by axelbaxel on 2009-07-02
yes and yes.

---

### Post by merlinus on 2009-07-02
Did you check the disk for errors from the opening menu?  If so, then it may be your dvd drive.  Check the disk on another computer.

Also, is there a safe video mode option (press F4 at the opening menu)?

---

### Post by axelbaxel on 2009-07-02
I tried that too, but with the same result as the other options.
Also, for me (as someone that knows almost nothing about hardware) it sounds weird that it worked perfectly for lot's of other programs, including windows.

E: Gonna try the safe video mode.

---

### Post by merlinus on 2009-07-02
I would suspect your sli dual nvidia setup, but the alternate install does not care about that.  Is your hdd sata?

---

### Post by axelbaxel on 2009-07-02
Yes, it is. It's a SAMSUNG HD502IJ if you need to know.

---

### Post by merlinus on 2009-07-02
I have read in a fewe posts that sata has to be disabled in bios in order to install.  You might do a search in the forum and on google, though.

---

### Post by axelbaxel on 2009-07-02
Actually, I'm not that sure about it being SATA anymore, because after several restarts, I noticed it saying I have 1 IDE Hard Disk and I only have 1 disk.

---

### Post by merlinus on 2009-07-02
Are you trying to run and install the 64 or 32-bit version?

---

### Post by axelbaxel on 2009-07-02
32bit.

---

### Post by merlinus on 2009-07-02
I am out of suggestions at this point.  Both 64 and 32-bit versions should work for your specs.  

Again, I wonder about the sli dual nvidia setup, but since the alternate install cd is text-based, it should be irrelevant. 

There may be some defects with your dvd drive.  Try the cds on a different machine to obviate that possibility.

---

### Post by axelbaxel on 2009-07-02
they worked on another machine, but why should exactly ubuntu have this problem while dozens of other Programs worked?

---

### Post by merlinus on 2009-07-02
A $64 question...

If everything we wrote about was tried -- md5sum, burning at 4x or slower speed, alternate text-based install disk which worked on another computer -- I have no answer.  Sorry...

---

### Post by axelbaxel on 2009-07-13
I tried again today, and this time I tried installing with apci=off and it worked. Would not have imagined it being that easy..

---

