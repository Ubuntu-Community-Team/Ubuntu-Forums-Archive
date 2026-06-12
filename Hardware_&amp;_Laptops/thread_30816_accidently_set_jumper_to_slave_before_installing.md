---
title: "accidently set jumper to slave before installing"
date: 2005-04-30
forum: Hardware &amp; Laptops
---

### Post by hornblower on 2005-04-30
When I installed Hoary, I put a larger hard drive in my computer. It's the only drive on its IDE channel, so I didn't pay much attention to the jumpers on the drive. Turns out, it is set for slave. I tried just to switch the jumper to master, but then i get kernel panics. So my questions are:

1. Should I even bother with changing this drive to master from slave (it is the only drive on its channel)?

2. If I should bother, what configuration work do I need to do to not get a kernel panic?

---

### Post by skoal on 2005-04-30
If at all possible, use the CS (Cable Select) jumper.  Most modern IDE cables (included with the motherboard) use a specific signal for UDMA/66+ drives (that is, UDMA66-133).  That's the easiest sol'n especially when you add a second drive.

If you're working with older cables/drives, set them drive jumper to Master.  Some BIOS(s) won't even detect your drive if that jumper is set to slave and attached to the end of the IDE ribbon.

* I assumed your kernel panic was just coincidental when you switched it to Master from Slave.  However, assuming you first noticed this kernel panic *immediately* after you changed the jumper and tried to boot, then the install may have recognized your drive as hdb (not hda).  I guess that's possible.

1. What does your partition information look like for that drive?
2. Post your 'menu.lst' in the /boot/grub/ path.
3. If possible, post what the lines during init which show the kernel panic information.

Possible Sol'n:

After you correctly set your jumper to Master or CS, it may be a simple matter of reconfiguring grub with a 'root'>'setup' thing a majigger and a minor edit of your 'menu.lst'.  After you post that information, I can show you how to make those changes.  A simpler sol'n may be just a re-install of Ubuntu after you make the correct jumper switch, omitting the format of specific partitions you want to keep (like /home).

---

