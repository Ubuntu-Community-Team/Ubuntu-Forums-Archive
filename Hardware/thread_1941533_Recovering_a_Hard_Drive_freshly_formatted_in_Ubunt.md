---
title: "Recovering a Hard Drive freshly formatted in Ubuntu 11.10"
date: 2012-03-15
forum: Hardware
---

### Post by Kingspec on 2012-03-15
Hey guys, 

I know this can seem quite mundane, but I, uh.. formatted the wrong hard drive, and I REALLY want that info back, preferably pretty much 100%...

I am only 4 weeks into Linux use, and I have no idea where to turn.

Anyone be nice enough to show me where to find this info?

Thanks in advance

---

### Post by varunendra on 2012-03-16
Boot with live cd, get connected to internet, install testdisk:
```
sudo apt-get install testdisk
```
run testdisk:
```
sudo testdisk
```
follow the instructions. A step-by-step guide for testdisk: [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Post back with details if any of the steps seems confusing. Incorrect actions may risk the recovery of data, so if you have got an external drive with enough empty space (larger than the size of the hard-disk), create an image of the target hard-disk before trying anything else.

That said, recovering partitions from an accidental formatting is really easy with testdisk or any other similar tool.

Oh, and did I say- "Welcome to the forums!" :)

Good luck with the recovery.

---

### Post by Kingspec on 2012-03-16
This is fantastic! The best part, is that it was my backup hard drive with all the family pictures (hence not wanting to lose it), so I have ubuntu loaded already on the PRIMARY Hard drive. So this should be fun!

I will keep you posted.

By the way, thanks for the welcome! Looking forward to be active in this forum, as Windows is faaaar in my rear view mirror. :)

---

### Post by varunendra on 2012-03-16
> **Kingspec said:**
> This is fantastic! The best part, is that it was my backup hard drive with all the family pictures (hence not wanting to lose it)..If it is (currently "was") the only copy of those pictures, be careful with whatever you do to the partition. DO NOT PERFORM ANY OPERATION that "Writes" to the disk, unless you are absolutely sure of what it'll do.

However, since it is a backup disk, I assume you already have another copy of the those pics somewhere else. If not, BE CAREFUL! I'll be glad to provide step-by-step instructions if needed.

**_PS_:**
Every OS has its pros and cons. So be sure to create a backup of your windows that you can restore later if required, before kicking it out if you're planning so :). Having the installation media is great. Else you can use some disk/partition imaging tool like clonezilla to 'image' the current installation.

---

### Post by Kingspec on 2012-03-16
That is precisely what I did, actually. I formatted my main, gave 100 gig to windows, 250 to Linux and 150 to ntfs blank. 

Then I have a separate Hard drive for backup.  that's the one i formatted by mistake...

But this works like a charm, got everything back! everything!

---

### Post by Kingspec on 2012-03-16
Thank you so much varunendra! You're a digital photo life saver!

---

### Post by varunendra on 2012-03-16
> **Kingspec said:**
> Tgot everything back! everything!
Sweet! And it's a pleasure to get something solved :)

---

