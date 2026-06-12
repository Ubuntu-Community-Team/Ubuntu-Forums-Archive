---
title: "Problems with newly built computer! =("
date: 2008-06-16
forum: Hardware
---

### Post by dupe576 on 2008-06-16
Ok.  So I spent this weekend ripping my hair out building my new computer.  After many frustrating hours.. i finally manged to get it booting up.  The only problem is I can't get ubuntu live cd working when my hard drive is plugged in!  It boots just fine when the hard drive is unplugged, but as soon as I plug it back in and boot back up is when the sh*t hits the fan.  

I've tried it with two different versions of ubuntu, many different cds, and even xubuntu.. All of them failed.. some more gracefully than others (xubuntu at least took me to some form of command line).  Ubuntu 8.04, however, gave me probably the most meaningful error message (repeated across my screen thousands of times) :

SQUASHFS error: sb_bread failed reading block 0x.....
SQUASHFS error: Unable to read page, block 0x....

I have both the cd rom and hard drive plugged in with one PATA cable.  The cd rom is set to slave drive.  I also tried reversing it and making the cd the master.. to no avail.  Both the hard drive and the cd rom were working just fine prior to me replacing the rest of the parts.  So I don't see why that would be a problem.  The only thing different is they used to have 2 separate PATA cables connecting them to the motherboard instead of a shared one.  The hard drive still has ubuntu/xp dual boot set up on it.

I've been googling around in kernel code trying to figure out whats going on and haven't gotten to the bottom of it yet.  As far as I can tell squashfs is some sort of compressed file system that the live cd uses.  And the function sb_bread is some sort of function for getting a buffer head to a block in the superblock of a file system.  But i'm not exactly how these two things are related to each other.

I'm going to try an external cd rom tomorrow to see if them sharing the PATA cable could make some sort of difference.  If that doesn't work i'll try a different hard drive instead.  In the mean time, does this make sense to anyone else?! Someone please help!

---

### Post by tenmoi on 2008-06-16
Run the cd check to see if it is good. Burn the cd at x4.

---

### Post by Winawer on 2008-06-16
The CD thing is often the first thing to get suggested, though I have no idea why since I've never seen anyone write back with "Whoops, yeah, my CD was crap...".  And yet, maybe I've missed a whole bunch of threads on that.

I'm under the impression that Ubuntu doesn't handle IDE (=PATA) drives very well under some hardware combinations;  for instance, I've read a number of posts about Marvell's IDE controller on ASUS motherboards which doesn't seem to be supported.  On the last build I did, I finally had to switch to SATA drives to get Ubuntu to work;  unless someone can suggest a specific fix for your problem, you might have to do something similar.

---

### Post by mal on 2008-06-16
Have you checked that the hard drive is being properly recognised by the BIOS?  Also, what is the boot order?  It may be that your system is trying to boot from the hard disk when it is attached.

Mal

---

### Post by waspbr on 2008-06-16
I find this a little odd, I have ubuntu running on two oldish computers, both with asus motherboards and both with IDE harddrives.... and no problems here so far

---

### Post by dupe576 on 2008-06-16
Hey guys, 

Thanks for the quick responses!  I appreciate the interest.  I just tried burning one at a lower speed and still no luck.  These cds boot up just fine when the hard drive isn't plugged in and they also work just fine on my laptop, so I'm not sure how that could be the problem.  HOWEVER, when i run an error check on the cd it says "errors found in 2 files!"  So maybe it is...

Maybe i'll try using a different burner.  

I still haven't had access to another cdrom or hdd so I haven't tried replacing those yet, but I will post the results when I do!

Oh, and yes, BIOS does detect both the hard drive and cdrom.  It reports the correct size, etc.

---

### Post by dupe576 on 2008-06-16
Oh yes, and the boot order is cdrom first.  Its definetly booting off the cd because ubuntu does begin loading, it just fails before I get to the desktop.

---

### Post by aimpau on 2008-06-16
Since its in IDE, make sure that your CDROM is jumpered as a slave and your HD is a master.

---

### Post by dupe576 on 2008-06-16
Yeah.. the cd is slave.  hd is master.  I tried the reverse too and no luck.

---

### Post by paulisdead on 2008-06-16
Have you double checked the hard drives jumper settings?  The jumper might be different for Master with Slave Present, and Master Without Slave Present.  I can guarantee if it's a Western Digital hard drive, the jumper settings are different for with a slave present, and without a slave present.  Also, if you've been using the cable select jumper setting, try manually setting them to master/slave.  Hell, if you haven't tried it you might even try setting both drives to cable select.

Just to make sure, you're putting the master drive on the end of the cable farthest from the motherboard, and the slave is the one in the middle of the cable?

If it's one of those Jmicron controllers, you might want to look into switching to SATA drives, those controllers can be trouble in Linux.

---

### Post by dupe576 on 2008-06-16
Well.. I seemed to have solved the problem!  It turns out it did have something to do with both thsoe drives sharing the PATA cable.  I don't know why exactly, but it works perfect now that I'm using a SATA cdrom drive.

Anyways.. cost me another 65 bucks for another cdrom but at least its working!!

---

