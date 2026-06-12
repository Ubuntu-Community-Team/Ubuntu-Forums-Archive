---
title: "[!!] Partition disks error"
date: 2006-01-10
forum: Installation &amp; Upgrades
---

### Post by bjhess on 2006-01-10
I'm in the process of building a NAS server and a automated backup server on Ubuntu Breezy 5.10 Server install.  My question is in relation to one of the machines - an old one.

My backup server is on a Intel Celeron 333 MHz with 64MB PC100 RAM.  It has an 8GB Seagate Medalist 8420 hard drive.  I'm planning on getting a hold of more PC100 RAM - most likely at least a 128MB stick.  But I wished to get hacking on this thing as soon as I could.

The install cruises (as much as it can) until I get to the partitioning of hard disks.  Well, I never get there.  The error is:

```
[COLOR="Red"][!!] Partition disks[/COLOR]
      [COLOR="Blue"]???   ???[/COLOR]
<Go Back> <Continue>
```

If I click "Go Back" or "Continue", I simply end up back at the same screen.  Indefinitely.

Could this have anything to do with the RAM deficiency?  Or is it more likely an incompatibilty with the hard disk?  If the latter, how can I get things running or is Ubuntu just "out"?

I might be able to try another hard drive in there in a couple days, but I figured I'd but this to the forum.  The current hard drive has Windows 98 installed, and it does boot up A-OK to that OS, so the drive should be working.

Thanks for the help!

Barry

---

### Post by Sef on 2006-01-11
Do you have a Breezy Live CD handy or another Live CD with a partitioner?  If so, see if it can partition your hard drive. If so, then the problem is with your install disk.  If not, then likely there is a problem with the hard drive.

---

### Post by bjhess on 2006-01-11
[QUOTE=Sef]Do you have a Breezy Live CD handy or another Live CD with a partitioner?  If so, see if it can partition your hard drive. If so, then the problem is with your install disk.  If not, then likely there is a problem with the hard drive.[/QUOTE]

Yes, I do have a Live disc on hand.  I can try that when I get home from work.  I will mention, though, that I tried two separate Breezy install discs.  One mailed from Ubuntu and one I burned myself.

---

### Post by Greg2 on 2006-01-11
You may want to try the System Rescue CD to partition and reformat before you use the Ubuntu install CD? I have used it with success on everything from 333mz 4GB systems to 1800mz 120GB systems with multiple drives, both desktop and laptop with ram from 128MB to 1GB.

The iso image is here:
[http://www.sysresccd.org/download.en.php](http://www.sysresccd.org/download.en.php)

You simply boot from the CD and hit ‘enter’ at the message Boot, Then when you get a command prompt enter:

```
run_qtparted
```

If you have never used QtParted you should read the manual first.

---

### Post by bjhess on 2006-01-11
It doesn't quite make sense to me that Ubuntu Live would allow me to partition a disk.  In any case, I didn't see an option to partition with Ubuntu Live (unless you're saying somewhere in the GUI - which has no chance of loading on this machine).

I'm now trying qtparted.  Pretty confident in that, though I'm unsure as to whether, after partitioning, Ubuntu will recognize the drive.  We'll see!

Thanks for all your help!

---

### Post by bjhess on 2006-01-11
qtparted worked wonders.  Well, sorta.

I cleared all existing partitions on the drive.  Then I began adding my partitions.  Once I tried to add the second partition qtparted would crash.  Tried several times.

My theory, then, was just to create one big primary / partition.  Then I restarted, booting with the Ubuntu install CD.  Server install progressed and I was able to restructure all of my partitioning with Ubuntu's utility.

THANKS for the tip!

Barry

---

