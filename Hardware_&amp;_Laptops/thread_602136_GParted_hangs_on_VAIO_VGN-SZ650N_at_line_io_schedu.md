---
title: "GParted hangs on VAIO VGN-SZ650N at line: io scheduler cfq registered"
date: 2007-11-03
forum: Hardware &amp; Laptops
---

### Post by bluecub22 on 2007-11-03
I have searched throughout the Ubuntu forums and on the internet before posting this message.

I have a brand new VAIO VGN-SZ650N.

Before installing Ubuntu 7.10, I'm running gnome Gparted LIVECD to partition a section of the harddrive as ext3. I'm booting gnome from the cd.

Trouble is, it hangs with any boot option on this line:

     "io scheduler cfq registered"

I've searched for hours and found it's probably connected with ACPI and bios settings. But I cannot access advanced bios settings in this laptop (just basic bios boot settings with the normal F2) Does anyone know if there's more bios settings availble some other way?

I've also tried several commands with during the gparted livecd boot sequence that have been recommended in other posts.

Does anyone else have this problem?
How can I disble ACPI in the bios?  I've tried to disable it in the livecd boot command line.

I look forward to any suggestions! This is my first forum post.

Raphael

---

### Post by tokker73 on 2007-11-06
I have the same problem on an Acer Travelmate 4720.

---

### Post by gbinal on 2008-04-27
I recently experienced the same problem laid out here and spent a good bit of time searching for answers here and elsewhere, to little avail.  Surprising since we are all registering the same symptom - 

Here's eventually how I worked around it.  When you boot into gparted, **there are a number of different choices for which configuration to use** - I always used the default, automatic configuration successfully until I hit this bug.  

**I eventually tried each of the other alternatives and found one that worked for my machine, i.e. ran successfully.  .**  All but two of the configurations gave me the same io scheduler cfq problem.  It will be clear when you find one that works for you as gparted successfully gets past the point at which it had been hanging and loads.  

(Note, you may be prompted to choose a couple of settings - you will be told what the defaults are - just use them for convenience.)


P.S.  I also recommend burning a copy of [Knoppix]("http://www.knoppix.net/") just to have around anyway, but it includes a partition editor and can be another route to try.  

*This taking place on a System76 Serval Performance laptop - a brand I strongly recommend, by the way.

---

