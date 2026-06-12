---
title: "Windows 7 / Karmic dual boot problems"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by goseph on 2009-11-02
I'd like to dual boot Karmic with win7.

My HD was previously entirely owned by Jaunty, I have formatted all to NTFS now using my gparted on the karmic live CD but still my computer fails to boot from the win7 CD (the same CD is recognised fine by my computer running Vista). 

Any ideas?

Possibly of relevance: My HD is 60 GB, however having deleted all ext3 / SWAP partitions and created a single new partition of NTFS, gparted recognises a single NTFS partition taking up the whole disk but says that the disk is only 55.89 GiB

Possibly of relevance: Format to NTFS only takes 4 seconds.

Thank-you all in advance for being awesome!

---

### Post by Earl_Maroon on 2009-11-02
Try deleting the partition and try again with blank disk space. The Windows installer will format/can partition the disk anyway. I think Windows installation disks don't like NTFS partitions they don't identify as fully working installations - my flatmate had a similar problem to you.

Also, regarding the disk size, the difference is because HDD manufacturers measure space differently from computers in order to make their products seem bigger. The manufacturer measures 1KB as 1000B and a computer measures 1KB as 1024B (1KiB)...

Oh, and gparted doesn't wipe your disk, it just defines the partiton, declares the space free and of that FS type. Most if not all data on the disk remains unchanged, but is made inaccessible as it isn't indexed... so it's normal for the process to be very short.
In contrast, when Windows formats a drive 0s are written.

---

### Post by goseph on 2009-11-02
Unfortunately, no joy.

I used gparted to delete my partition and then tried booting from the windows 7 CD.

After a very long time of a single flashing underscore I got:

GRUB loading
error: no such partition
grub rescue >

---

### Post by EJeanmaire on 2009-11-02
> **goseph said:**
> Unfortunately, no joy.

I used gparted to delete my partition and then tried booting from the windows 7 CD.

After a very long time of a single flashing underscore I got:

GRUB loading
error: no such partition
grub rescue >

You need to enter the BIOS and make sure that your first boot device is the CD-ROM drive... not the harddrive.  Sometimes you can press F8 or something to choose a device to boot from on the fly at startup, pick cd-rom.

---

### Post by goseph on 2009-11-02
> **EJeanmaire said:**
> You need to enter the BIOS and make sure that your first boot device is the CD-ROM drive... not the harddrive.  Sometimes you can press F8 or something to choose a device to boot from on the fly at startup, pick cd-rom.

It already is, it boots the Karmic Live CD just fine.

---

### Post by EJeanmaire on 2009-11-04
> **goseph said:**
> It already is, it boots the Karmic Live CD just fine.

Did you change the boot order of your hard drives (maybe you unplugged them? switched them around, plugged in a USB stick or external drive)?

---

### Post by goseph on 2009-11-04
> **EJeanmaire said:**
> Did you change the boot order of your hard drives (maybe you unplugged them? switched them around, plugged in a USB stick or external drive)?

No nothing like that unfortunately :(
I put the karmic CD in my laptop.. no problem
I put the win7 CD in my other computer... no problem

I put the win7 CD in my laptop (where I want it to boot) ....nothing!

---

### Post by Mark Phelps on 2009-11-04
> **goseph said:**
> No nothing like that unfortunately :(
I put the karmic CD in my laptop.. no problem
I put the win7 CD in my other computer... no problem

I put the win7 CD in my laptop (where I want it to boot) ....nothing!

The Win7 "CD" is not a "CD", it's a "DVD".  The Karmic CD is a "CD" and your other machine can apparently read DVDs.

So, do you know for sure that this machine can read DVDs?

---

### Post by goseph on 2009-11-05
> **Mark Phelps said:**
> The Win7 "CD" is not a "CD", it's a "DVD".  The Karmic CD is a "CD" and your other machine can apparently read DVDs.

So, do you know for sure that this machine can read DVDs?


Good point about windows 7 being a DVD but yes, my laptop definitely plays DVDs

---

### Post by Mark Phelps on 2009-11-05
> **goseph said:**
> Good point about windows 7 being a DVD but yes, my laptop definitely plays DVDs

Is this the original MS-provided DVD, or is it a copy that you (or someone else) made?  Asking because if it's a copy, it could have defects because it was burned at too high a speed, or the media is not the best.  If it's an original, it's a mystery as to why IT won't read when movie DVDs can be read.

If you can't easily replace the CD/DVD drive in the laptop, you could try buying a CD/DVD cleaner and seeing if cleaning the laser lens makes any difference.

Don't know what else to suggest, sorry.

---

