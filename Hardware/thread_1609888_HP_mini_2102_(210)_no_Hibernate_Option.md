---
title: "HP mini 2102 (210) no Hibernate Option"
date: 2010-10-30
forum: Hardware
---

### Post by VideoRoy on 2010-10-30
I searched a bit but did not find this exact problem.  I am running an HP 2102 same hardware as 210 and I do not seem to have a Hibernate option in MM 10.10.  It works in the dual boot Windows so I know is possible but I do not seem to be able to find the option

I have 2gb of memory so I setup a 4gb swap so should have plenty of space.  I just setup a laptop for someone else and it works there so I know it is possible in this version of the kernel 2.6.35-22.

Any suggestions on what I might have missed.

---

### Post by VideoRoy on 2010-11-07
Finally got back around to this problem after fixing a bunch of other stuff.  Turns out I did something stupid of course.

My swap is 4mb not 4gb :rolleyes:.  That is what you get when you hurry.

My install has 3 partitions /, /home and /swap.  I have been researching how to backup since I have put in a lot of manual tweaks to get everything working but I was wondering if I could just shrink my /home with Gparted and recreate /swap to be bigger.

I do this all the time in Windows but in Linux is it really that easy?

---

### Post by VideoRoy on 2010-11-07
For the sake of completeness, it is just as simple as resizing /home and /swap.  Once I did that I restarted and Hibernate is now an option and seems to work just fine.  Note to resize Swap you need to Swapoff from the menu then Swapon when you are done.

One note: I have never gotten GParted to work for me if I boot from a GParted live CD ... never!  I got close one time on a desktop machine but on laptops or other computers is always pukes even with the most recent version.  Lots of errors on the screen this time it said could not find a screen but I am reading it from the screen.

Any way boot from Ubuntu Live CD and run GParted from there always works.  I am sure the hardware drivers are better integrated by design in Ubuntu but just wanted to mention that in case some needs to do this.

The other thing that helped me was I made sure /Swap was at the end of the partition when I did my partitioning.  Probably not a show stopper but this allowed me to stay contiguous on the disk so as not to have unnecessary thrashing.

---

### Post by nixahn on 2011-08-28
I posted something wrong and can't delete the post now;

---

