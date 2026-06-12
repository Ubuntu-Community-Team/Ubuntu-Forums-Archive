---
title: "Maximum RAM seen by Ubuntu 7.10"
date: 2008-01-30
forum: Hardware &amp; Laptops
---

### Post by circum on 2008-01-30
I have a desktop system with 4 gigs of RAM (confirmed by bios tests). Nonetheless, Ubuntu 7.10 appears to see only 3.1 gigs. Here is what I find in /proc/meminfo:

MemTotal:      3107576 kB

Some other threads indicated that Ubuntu (like other 32 bit systems) can handle only 4 gigs of RAM, including the swap file. This must be incorrect as my computer's swap file is 6 gigs in size.

So, my question is, why does Ubuntu 7.10 see only 3.1 gigs where there are 4? And how can I change this behaviour?

Benoît Gauthier

---

### Post by oldsoundguy on 2008-01-30
before you go blaming the system, check how much is shown in BIOS.  You may have on board video and sound and that is eating up allocated memory.

---

### Post by gruss on 2008-01-30
osg makes a good point might have some other stuff eating it up, if you utilize 4 gigs of ram why not go for the 64 bit version?  Maybe I'll pick up 4 gigs of ram for the notebook and see if it reports all 4 and report back ;)

---

### Post by circum on 2008-01-30
I checked the BIOS settings and nothing suggests that memory is stolen in the boot process. Maybe the video card grabs memory (900 megs???) but how can I establish that?

Is there a way to low-level investigate what is using the RAM?


Benoît Gauthier

---

### Post by oldsoundguy on 2008-01-30
ON BOARD video will take memory from the basic system.  Bios in no way will tell you that.  Really depends on the on board chipset as to how much memory it will hog.  (why plug in cards with their own memory are sooooooo much better!!)  Most I have ever seen though was grabbing 64 meg of ram .. but the newer set ups may take more.  Same with the built in audio .. 64 meg is the most I have seen .. not saying that some chips will grab more, just that I have never seen one that did. 
What that boils down to is that something is taking your memory or IT IS DEFECTIVE.  On the Ubuntu LIVE disk is an option to test your memory .. I would do just that.

---

### Post by Yellow Pasque on 2008-01-30
> MemTotal: 3107576 kB
That sounds a lot like 3.2GB, the barrier for 32-bit systems. It's time for a 64-bit OS. You can keep your /home partition (if you have a separate /home partition) and do a fresh install with Ubuntu64.

> Some other threads indicated that Ubuntu (like other 32 bit systems) can handle only 4 gigs of RAM, including the swap file. This must be incorrect as my computer's swap file is 6 gigs in size.
How did you get a 6GB swap partition? It sounds like the installer just made it twice the size of your RAM.

What do you get from this command?:
```
free -m
```

---

### Post by oldsoundguy on 2008-01-30
Temujin .. thanks for the info on the 32bit .. I did not know that!

Personally I can not see the need for that much ram for most of the work I do, but I guess if you game, that could be a consideration.

"Because it's there is only an excuse for climbing mountains!"

---

### Post by circum on 2008-01-31
> **Temüjin said:**
> That sounds a lot like 3.2GB, the barrier for 32-bit systems.

Isn't the limit of 32-bit systems 2^32 bytes or 4,294,967,296 bytes or 4 gigs?

> How did you get a 6GB swap partition? It sounds like the installer just made it twice the size of your RAM.

That appears to be the case indeed.

> What do you get from this command?: free -m

             total       used       free     shared    buffers     cached
Mem:          3034       2461        573          0         85       1997
-/+ buffers/cache:        377       2657
Swap:         6236         34       6202


Benoît Gauthier

---

### Post by circum on 2008-01-31
> **oldsoundguy said:**
> ON BOARD video will take memory from the basic system.

According to an article on this motherboard (ASUS Mother Board P5K-VM) [http://www.anandtech.com/mb/showdoc.aspx?i=3111&p=2]("http://www.anandtech.com/mb/showdoc.aspx?i=3111&p=2"), there is on-board video (although there is no connector at the back of the computer...), on-board sound and on-board LAN. IN don't see that this would amount to 900 megs, though. I added a nvidia GEforce 8 series video card.

> What that boils down to is that something is taking your memory or IT IS DEFECTIVE.  On the Ubuntu LIVE disk is an option to test your memory .. I would do just that.

No error identified during a memory test. Also, one of my colleagues has the same specs (quad CPU, 4 gigs or RAM) but a different motherboard and he gets the same amount of available memory after booting Ubuntu (although his swap partition if 9 gigs in size).


Benoît Gauthier

---

### Post by skunkTrader on 2008-04-16
I have 4GB installed in a Dell workstation. My 7.10 install can see MemTotal:3635920 kB

---

### Post by circum on 2008-04-16
My original post dates. Since then, I have uncovered that Ubuntu 32 bits allows to address up to 4 gig of RAM minus whatever the hardware steels (such as the video card). With 4 gigs of RAM on board, what Ubuntu sees is all you can get -- it's got nothing to do with Ubuntu.

To get more available RAM, you must first add physical RAM and then either compile a new version of Ubuntu with PAE (Physical Address Extension) support or move on to the 64-bit version of Ubuntu. I did recompile Ubuntu with PAE support and that version did see all 8 gigs of RAM I now have on board. However, there were issues with the Nvidia video drivers.

I have tested the boot CD version of Ubuntu (7.10) 64 bits and it worked like a charm: all 8 gigs available and a working video driver right off the CD. I will try to install that version for real within the next few days.

Benoît Gauthier

---

