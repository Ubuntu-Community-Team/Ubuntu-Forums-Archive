---
title: "Problems Formatting HDD"
date: 2005-12-14
forum: Installation &amp; Upgrades
---

### Post by Roger Rabbit on 2005-12-14
Hey All

I currently have Ubuntu 5.04 running on my computer but I need to format the harddrive so I can reinstall windows (I know, it sounds criminal doesn't it but I never intended to run Ubuntu on there permanently as I have a seperate Linux PC).  My CD-ROM is the primary boot drive and I loaded up the computer with the HDD driver disc inserted in the drive so I could format.  When the computer loads, however, it doesn't boot from the disc.  I know for definite the disc works because I've used it before.  Is there any other way to format my HDD, perhaps from the terminal in Ubuntu or something.  Sorry if this is a bit of a newbie question!

Thanks,
-Andy

---

### Post by Zelut on 2005-12-14
if you are reinstalling windows you should be doing your formatting from the windows installation CD.  Sounds like, maybe, your BIOS just isn't checking the CD for boot BEFORE the HDD.  Take a look in your BIOS, make sure, and reboot with your windows installation CD.

...and yes, it does sound criminal :)

---

### Post by Roger Rabbit on 2005-12-14
ok, in BIOS, ive tried every configuration I can for the HDD and CDROM.  ive had the HDD as a slave to the CD, HDD as primary 1 and CD as Primary 2 etc etc.  When I put the Windows boot disc in, it starts the formatting process...then fails :( .  I'll try it again and post back to let you know whether it's working.  Thanks for the help...

---

### Post by Zelut on 2005-12-14
wether the HDD or CD is the slave/master shouldn't be the issue.  The point I was referring to was making sure it was CD then HDD in the boot sequence.

...as far as the format failing I wouldn't know what to tell you on that.  It's windows, who knows how to troubleshoot that stuff.  Call MS tech lol.

...or, you could try booting from a liveCD and using gparted (in gnome) to partition your HDD.

---

### Post by Roger Rabbit on 2005-12-14
ok sorry to double post here, but ive just tried booting again...

> Setup cannot install Windows on your computer.

A disk error was detected while writing a new boot record to your first hard disk.

Oh, on another note, I set the HDD as a slave to another computer and tried to format that way.  It couldn't format there either because the format of the HDD was "RAW".

---

### Post by BatsotO on 2005-12-14
Have you try to zero filling the drive?
I recommend Ultimate boot cd if you can boot from cdrom. It have many tools. The one i find most usefull are maxtor zero fill and setup tools (format and set up mbr) coz mostly use maxtor.
But this week i also have somekind of same problem with hard drive. I cant format it. cant even delete the partition or zero filling it, but i dont think the drive is in good condition (bought it a year ago or so but been working 24/7).

---

