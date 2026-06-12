---
title: "Bios is fried... maybe.  Can I flash it in Ubuntu?"
date: 2009-09-10
forum: Hardware
---

### Post by dodle on 2009-09-10
Recently my power supply passed away and took two hard drives with it.  I have now found that I cannot boot from a hard disk.  I just installed a fresh copy of Ubuntu but can't boot it up.  Here is my board with the bios update: [PT88AS](http://mach-speed.net/support/index.php?option=com_content&task=view&id=181&Itemid=44).  I guess it is possible that the bios chip is screwed up and wanted to see if updating it would fix the problem.  Is there a way to do this in Ubuntu, more specifically a liveCD of Ubuntu?

---

### Post by khelben1979 on 2009-09-10
Have you checked in what order devices are chosen for boot up in BIOS?

---

### Post by GoldenSun on 2009-09-10
Every time I had a psu go out in a rage, I find that it takes the mobo with it.  Check all the capacitors on it to see if any of them are leaking, bulging, or popped open.  

Also I have another mobo, and it appears to be in good condition.  But it will only boot once in fifteen or so tries.  So something could have fried, but looks totally fine.

I doubt your bios is the problem.

---

### Post by dodle on 2009-09-10
By default the boot order is floppy, hard disc, cd.  But I changed it to cd, floppy, hard drive.  No disc in either the floppy nor cd, and still it fails to boot from hard disc.

I will take a look at capacitors in a little bit.  Also, I forgot to mention that the POST is extremely slow.  It takes probably 2 or 3 minutes to actually get to the booting.

---

### Post by dodle on 2009-09-10
Thanks GoldenSun, I opened up the computer and found a single bulging capacitor.  I'll replace this tomorrow and I'm sure it will be working fine again.  This will be the fifth capacitor that I've changed this week.

**Edit:** I went ahead and replaced the bulging capacitor, but with no effect.  I didn't notice any other problematic capacitors.  The POST is still extremely slow and I can't boot from a hard disk.  I only have one disk to try out at the moment.  I'll try another as soon as a part for it gets here.  But even if the other hard drive does work, that slow post is dang annoying.

---

### Post by markbuntu on 2009-09-11
If you found one bad cap then that usually means all the others are also going bad. Bad capcitors come in huge batches, whole production runs.

When they short out they can also burn out the traces on the board or take out some regulator chips which you will not be able to see.

Do the hds spin up?
Does the cd?

You could try reloading the bios from a cd if you can get it to boot.

---

### Post by dodle on 2009-09-13
I fixed my hard drive, installed it and everything started up fine and quick.  So I took a look at the hard drive that I had been trying to boot from... one of the pins is broken off.  Apparently that was what caused the slow start-up.  My motherboard is working great now.  

Thanks for the help.

---

