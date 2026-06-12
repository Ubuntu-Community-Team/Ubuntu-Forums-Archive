---
title: "Data recovery off failed Hard Drive?"
date: 2006-02-19
forum: Hardware &amp; Laptops
---

### Post by bascha on 2006-02-19
I have a friends 80GB IDE Maxtor hdd that has failed.  At first it wouldn't boot Windows XP and when I went to recovery console and did a chkdsk it came up with numerous bad sectors and unreadable segments and would quit half way through the scan.  I figured no problem, I'll recovery their data using linux (Knoppix this time cause that's what I had).  NO LUCK.  Was at first able to get to desktop (very slow) and then it would just lock up.  Now the disk is not even visable when I go into the BIOS.  I can hear that the disk powers up and is spinning and I've tried it as both a slave and master in a couple other computers. 

I've reinstalled XP Home :cry: on a new Seagate drive and they are up and running but I was still hoping to recover some data.  

Any suggestions or am I looking at a new paperweight?

---

### Post by dcstar on 2006-02-20
[QUOTE=bascha]
......
Any suggestions or am I looking at a new paperweight?[/QUOTE]
With hardware failures like that the best bet is to find a local data recovery service.

It may be a bit expensive, but you have to decide how valuable the data is.

---

### Post by bascha on 2006-02-20
My friend is pretty cheap but thanks for the suggestion.  I had done a backup for him about 6 months ago and I guess he will just have to deal with the loss.

---

### Post by jimmer on 2006-02-20
bascha,
If the drive is not recognized by your computers bios you're pretty much hosed. I had success only once in this situation. I had a Buffalo Linkstation NAS which I used as a central location of all my files. The drive wouldn't even spin up. I swapped out the Primary Controller Board with the same model number and size. The drive is now fine and still working. I got lucky, the same model hard drive usually has several different PCB revisions and different revisions are not cross-compatible. It seems that your drive does spin up and you did have it showing up in your bios. I would have initially thought it was just a software issue or a corrupted MBR. Knoppix was a good choice to use as a Live CD to get your data off. You could have even used the Ubuntu Live CD. I take it you checked the jumper settings and set the disk as master or slave correctly. I have also made the mistake of putting a drive on the secondary controller which was disabled in the bios. It was a good idea to move the drive to another computer because sometimes it's the hard drive controller which is faulty.  If your drive doesn't show up in your bios it will cost at least $250 and up for a data recovery service. Some will give a free quote or a small fee to diagnose then more money to repair. Most jobs cost around $500 and up. Good Luck!

---

### Post by bascha on 2006-02-22
[QUOTE=jimmer] I take it you checked the jumper settings and set the disk as master or slave correctly. I have also made the mistake of putting a drive on the secondary controller which was disabled in the bios. It was a good idea to move the drive to another computer because sometimes it's the hard drive controller which is faulty.  If your drive doesn't show up in your bios it will cost at least $250 and up for a data recovery service. Some will give a free quote or a small fee to diagnose then more money to repair. Most jobs cost around $500 and up. Good Luck![/QUOTE]

I checked the jumper settings and tried it as both the slave and master in 3 different computers and no luck.  Thanks for the info on estimated costs for data recovery services.  The data in this case is not that valuable to the individual but it is still good to know in case next time it is.

cheers,

---

### Post by linuxgrrl on 2007-05-31
This is too late to help your friend, but in case anyone finds this later ...
I had a similar problem  - heat damaged drive, machine would not boot and bios did not see the drive -- but FWIW, using the "load failsafe defaults" setting on my BIOS, I was able to get it to boot and stay up long enough to pull the data off the drive. 
Not sure why it worked, but what the heck.  Now trying to learn what SMART monitoring is about so this doesn't happen to me again! :)

---

### Post by Tilo on 2007-05-31
I would suggest to create an image file from the damaged harddrive, using dd_rescue
and then use whatever recovery tool you want to use on the image -- not on the drive. 
Keep the drive as a backup (untouched).

[http://www.unixgods.org/~tilo/disk_rescue.html](http://www.unixgods.org/~tilo/disk_rescue.html)

[http://www.garloff.de/kurt/linux/ddrescue/](http://www.garloff.de/kurt/linux/ddrescue/)

---

