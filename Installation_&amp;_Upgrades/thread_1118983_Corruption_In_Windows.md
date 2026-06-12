---
title: "Corruption In Windows"
date: 2009-04-07
forum: Installation &amp; Upgrades
---

### Post by rockstarrem on 2009-04-07
Hello,

I normally use the manual partition editor, I'm wondering if I use the guided partition editor will it automatically re-partition the Windows partition so it's friendly? Last time I couldn't even boot into Windows because chkdsk always came up and I always cancelled, and one time I rebooted while it was doing it because I'm impatient :P but yeah, will it resize it to a Windows friendly size so I don't have to go through chkdsk everytime I boot into Windows?

Thanks!

---

### Post by upchucky on 2009-04-07
based on very little information being given, I am assuming that you want to repair a non booting windows from within Linux if this is true then there is a utility package in linux called libntfs it has a program called ntfsfix that will get the windows shutdown/startup problem fixed.

ntfsfix does not actually fix inconsistencies but it cleans the NTFS filesystem Journal which enables the partition to be mounted again and able to read/write with ubuntu.

Also Knoppix is an awesome repair live cd that can rescue windows systems that are taken down either by viruses or the self destruct mode that microsoft thinks should be there.

gparted can resize partitions, but it does nothing to make partition friendly what ever that means.

to play with any operating system requires patience and lots of reading, this is why so many people are having trouble understanding computers, when windows came to be, they stopped teaching and said just point and click. well the only thing point and click is good for is operating a microwave.

please explain more and if we can help we will try.

---

### Post by Herman on 2009-04-07
It doesn't matter which option you use in the Ubuntu installer's partition editor, or in GParted, it will always tell your Windows system to run CHKDSK before it boots just to be on the safe side, especially if you use Windows with the NT File System.

It's good for the NT File System to have a CHKDSK and you should let it run until it finishes.

It should only be needed the first time you reboot immediately after Windows has been resized, and after that everything should be back to normal.

It's a good idea to run file system checks regularly on any kind of file systems, it keeps them in good order.

Regards, Herman :)

---

### Post by lisati on 2009-04-07
> **herman said:**
> it doesn't matter which option you use in the ubuntu installer's partition editor, or in gparted, it will always tell your windows system to run chkdsk before it boots just to be on the safe side, especially if your use windows with the nt file system.

It's good for the nt file system to have a chkdsk and you should let it run until it finishes.

It should only be needed the first time you reboot immediately after windows has been resized, and after that everything should be back to normal.

It's a good idea to run file system checks regularly on any kind of file systems, it keeps them in good order.

Regards, herman :)
+1

---

### Post by rockstarrem on 2009-04-08
Sorry if I was unclear, I mean I want to do a fresh install of Ubuntu now over Windows. So you're saying if I do this I'll only have to run chkdsk once?

Thanks.

---

### Post by lisati on 2009-04-08
> **rockstarrem said:**
> Sorry if I was unclear, I mean I want to do a fresh install of Ubuntu now over Windows. So you're saying if I do this I'll only have to run chkdsk once?

Thanks.

If you install Ubuntu over the top of Windows (which will replace Windows), then Windows will not be there to do a chkdsk.
If, however, you resize the partition containing Windows, and install Ubuntu in another partion, then Windows will automatically run chkdsk once the first time you re-start it.

---

### Post by rockstarrem on 2009-04-08
Right, but my question is will it run on every reboot?

---

### Post by lisati on 2009-04-08
> **rockstarrem said:**
> Right, but my question is will it run on every reboot?

No, only the first reboot, if there's a problem, or if you tell it to.

Did you notice I said it will run chkdsk **once**?

---

### Post by Herman on 2009-04-08
GParted puts a 'dirty' flag in any NTFS partition it works to deliberately  induce Windows to run a file system check on it the next time Windows boots.

Windows will normally run CHKDSK on it and that clears the 'dirty' flag.

If Windows is running CHKDSK at every boot-up, it could be a sign that something else is wrong. 
Try running CHKDSK /R manually, that might clear your problem.
If that doesn;t fix it then maybe your hard disk is on it's way out. If that's the case then you should probably run some tests to check on your hard disk. 
[Smartmontools]("http://smartmontools.sourceforge.net/") is a program you can install in Ubuntu to read the hard disk's error records, and we also have a prgram called 'badblocks' which can test your hard disk for weak sectors in case it's magnetic properties are beginning to fade. [Hardware Detection and Testing]("http://users.bigpond.net.au/hermanzone/p8.html#Hardware_Detection_and_Testing") (commands for).

GParted will only induce Windows to run CHKDSK once.

---

