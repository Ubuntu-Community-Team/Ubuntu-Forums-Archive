---
title: "Installation frozen - before it even started!"
date: 2009-01-09
forum: Installation &amp; Upgrades
---

### Post by purplegreendave on 2009-01-09
Trying to breathe some new life into an old laptop by installing Ubuntu 8.10 on it.
I've got to a screen that says:

**Welcome**
Ready to install? Once you answer...
...This language will be the default language for the final system.

Then there's a circle thing, which I'm guessing is like the hourglass in Windows.

Says "Step ? of 7" in the bottom.



It's been at that screen for like, 25 minutes.
Should I start it again?

The laptop has a 1.13Ghz Intel Celeron Proc, 256MB RAM, 15Gig HDD.
Is it too weak for Ubuntu? Should I try another (lighter) distro instead?
All I want it to do is have wifi, so I can access my network storage and play music back through my stereo, and from what I've seen/read/heard Ubuntu is the best for that?

Thanks for reading if you have ):P

---

### Post by overdrank on 2009-01-09
> **purplegreendave said:**
> 
It's been at that screen for like, 25 minutes.
Should I start it again?

The laptop has a 1.13Ghz Intel Celeron Proc, 256MB RAM, 15Gig HDD.
Is it too weak for Ubuntu? Should I try another (lighter) distro instead?
All I want it to do is have wifi, so I can access my network storage and play music back through my stereo, and from what I've seen/read/heard Ubuntu is the best for that?

Thanks for reading if you have ):P

Hi and welcome, with the 256mb of memory and the graphics of the laptop using a portion of that, you will need to use the alternate cd for the installation. It is a text based install. :)

---

### Post by purplegreendave on 2009-01-09
Yeah, I meant to add it has integrated graphics, dunno exactly what chipset.
All right, I'll give the text based installer a go

---

### Post by purplegreendave on 2009-01-09
I d/led the alternative media, but it's stuck at 33% of the partitioning process :(
Linux never works for me :p

> Creating ext3 file system for / in partition #1 of SCSI1 (0,0,0) (sda)...

---

### Post by overdrank on 2009-01-09
> **purplegreendave said:**
> I d/led the alternative media, but it's stuck at 33% of the partitioning process :(
Linux never works for me :p

Ok, are you trying to dual boot? You may have errors on the hard drive. You may also check the cd for errors.

---

### Post by purplegreendave on 2009-01-09
Nope, I ran gparted earlier and reformatted the drive as Fat32 - should I have used NTFS?
It was already a fat drive, so I just left it like that...

Running the memory test now, will check the disk for errors too.
In the meantime if you have any revalations, just swing 'em my way :D

Memory test turned up nothing...
Nor did cd test...

Will try again later.

---

### Post by overdrank on 2009-01-09
> **purplegreendave said:**
> Nope, I ran gparted earlier and reformatted the drive as Fat32 - should I have used NTFS?

Will try again later.

Hi and yes NTFS will not work, It will have to be ext2 or ext3 I believe, so you may want to try gparted again.
Edit you may also want to look in bios to see what amount of memory is being shared with the graphics.

---

