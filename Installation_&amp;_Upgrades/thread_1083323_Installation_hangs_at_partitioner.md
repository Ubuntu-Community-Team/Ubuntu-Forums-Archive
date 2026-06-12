---
title: "Installation hangs at partitioner"
date: 2009-02-28
forum: Installation &amp; Upgrades
---

### Post by aineo on 2009-02-28
I am trying to install Ubuntu 8.10 on a Dell Latitude D600 with 500MB of RAM and a 1400 MHz Intel Pentium M Processor.  Whether I use the LiveCD or the alternate CD, it hangs when it gets to the partitioner.  When I am booted into the LiveCD I can see the hard drive, but it is labeled "40.0 GB Media".  I cannot seem to read anything on this hard drive.  I am afraid this might mean the hard drive is hosed.  (Windows was blue screening and will no longer boot, which is what pushed me to install Ubuntu)  Any ideas?

---

### Post by sailthesea on 2009-02-28
Did you use the Manual / Guided option on install? I had a similar problem although I've only bypassed it for now by using wubi which you obviously can,t It should let you see the partition and edit it manually

---

### Post by aineo on 2009-02-28
I never get far enough to have that choice.  After I confirm the keyboard layout, it brings up a little box that says "starting partitioner".  That quickly goes away and then it just hangs.  It does something similar on the alternate CD.

---

### Post by sailthesea on 2009-02-28
Hmmmm Doesn't sound good if it does it with both discs
You could try making a live cd of Gparted or similar and see if you can get to partition with that It sounds like there isn't an existing partition for the install cd to use and you can't create one if windows is bricked Other than that I don't really know what you could do
Keep asking though someone will know!
Good luck and let me know how it goes

---

### Post by pmooney78 on 2009-02-28
Just a shot in the dark, but it might help ...

I had similar problems trying to install 8.10 until I tried installing without my iPod plugged into the computer at the time. I installed with the iPod physically disconnected and everything went fine.

My theory is that Apple's funky file-handling mechanisms on the iPod make the partitioner hang ...

---

### Post by aineo on 2009-03-01
I wish that were it.  There is nothing plugged into the laptop at all.

---

### Post by JNieto on 2009-05-01
Hello "aineo", 
  I was having EXACTLY the same problem (instalation hanging when entering the partitioner).
  I found this archived thread which gave me a hint: [http://ubuntuforums.org/showthread.php?t=531871](http://ubuntuforums.org/showthread.php?t=531871)
  Also, I could boot the Ubuntu 9.04 Live CD, but Gparted hanged if I started it. 
  
  The reason (in my case) was _a few bad blocks on XP C: drive, that I could mend with a CHKDSK from windows_.
 
"**aineo**": You are right, your hard disk is most probably damaged. I counsel you to google for a disk checker that you could boot (can Gparted fix damaged disks ???). Or buy a new (bigger) disk.

**Hint for the rest of "navigators**": before installing Ubuntu [COLOR=Black]disconnect all external storage an[/COLOR]d_ run a disk check_ on your Hard disk(s) (it can be done in M$-Win: right click on a drive->properties->tools...).

Best regards from Luxembourg
Jesús Nieto

---

### Post by SpeedyGonsales on 2009-05-02
What if install hangs using 2 disks? (I mean two tries, first with one disk, then unplugged it and plugged in another - also tried both alternative install 904 & 810)

I tried with 60GB PATA disk (in console I started dmesg, so it is recognized as /dev/sda, but partitioner doesn't find it).

I tried with 40GB PATA disk, dmesg also have found it, but partitioner hangs (tail /var/log/partitioner shows iterations, I have experience with Ubuntu from dapper, but never had problems installing it).

I tried both CD & USB install, intrepid & jaunty, and now I'm pretty much out of options :confused:

---

