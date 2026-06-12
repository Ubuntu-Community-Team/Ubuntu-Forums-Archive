---
title: "remove Windows"
date: 2009-10-04
forum: Installation &amp; Upgrades
---

### Post by ran1wil on 2009-10-04
everyday i learn to love ubuntu a little more and now i want to remove windows and extent the ubuntu partition im not a 100% on how to do this so i screan capped gparted.

---

### Post by Bartender on 2009-10-04
Have you made recovery DVD's yet?  If not, do it.  If you have, you don't need the HP recovery partition any more.

You don't want to just re-install Ubuntu?  You want to move it into the Windows area?

First things first - do a little googling and/or searching on this forum on how to fix GRUB bootloader.  When you wipe vista or XP you will also lose the little scrap of GRUB code that's installed to the Windows MBR.  So you have to be ready to fix GRUB right after you wipe Windows.  I haven't fixed GRUB before but there's about a million posts on the subject and it doesn't look hard.

Make yourself a GParted LiveCD (link under my sig).  The download is an .iso, so you have to convert the download to a bootable disc just like you would with an Ubuntu installer download.  When you're done you'll have a stand-alone partitioning tool.

Boot from the GParted LiveCD (GPLCD) and "remove" the Windows partition.  Apply the change.  You need to "Apply" each change as you go or the tasks will stack up and GPLCD will try to do them all at once.  

If you've made your recovery DVD's, remove the HP recovery partition too.  Apply the change.

Now "resize" the Ubuntu partition all the way to the left so that it swallows up that existing unallocated section, plus all space left from removing Windows.  Apply.  Since GPLCD will be moving data with this step, it will take a while.

Move swap all the way to the right.  Apply.  Then resize the Ubuntu partition again so that it nudges up against swap.

Then be ready to boot from a Super Grub Disc or the Ubuntu installer CD and fix GRUB.

That's probly the simplest that I can come up with.  Someone else will undoubtedly come up with a better idea :)

---

### Post by ran1wil on 2009-10-04
i have made the recovery cd's but dont think i will need the since im about ready to scrap the windows os ive been playing with ubuntu for about a year and had no real problems.i have a boot loader repair cd ready to go.i dont want to do a fresh install as i just moved all my pics and documents to ubuntu

---

### Post by Bartender on 2009-10-04
That's good that you made the recovery discs.  Even if you're sure you'll never want to use them, there may come a day when you want to sell the PC.  It'll be easier to sell with windows on it, or at least the option to put windows back on it.

---

