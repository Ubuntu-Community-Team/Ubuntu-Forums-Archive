---
title: "ESATA dock:  worked fine in Hardy, doesn't work in Maverick"
date: 2011-01-17
forum: Hardware
---

### Post by zkissane on 2011-01-17
I have a combo ESATA/USB external dock that I use for backups.  I have 2 hard drives that I rotate; one active, the other stored offsite.  I use it in ESATA mode, rather than USB, for speed.  In Ubuntu Hardy this worked perfectly.  I had to shut down the machine to swap the drives (in other words, I wasn't using it as hot pluggable) but I didn't care about that. I do remember using UUIDs in /etc/fstab for it but I don't remember the details (maybe the UUIDs for both drives mounted in the same place) 

My ESATA "card" is just a breakout plate that plugs into an internal empty SATA port on my motherboard. 

I upgraded to Maverick today (OS is on a separate internal disk) and it will not recognize the drive in the ESATA dock at all.  fdisk, lshw -C disk, nothing show the disk at all, so obviously I don't get a /dev/sd* assignment.  The BIOS recognizes the disk just fine, but that's it.  If I take the drive out of the dock and plug it directly in to the motherboard SATA port it works just fine; in fact I restored my SVN repository off of it without a hitch.  Again, I am putting this drive in the dock before I boot the computer, so it's not an issue of trying to hot plug the thing.

I saw this post, and it describes my problem almost perfectly (he even uses his dock for the same reason I use mine):
[http://ubuntuforums.org/showthread.php?t=1635708](http://ubuntuforums.org/showthread.php?t=1635708)

but there was no resolution that I saw.  Does anyone have any suggestions?

---

