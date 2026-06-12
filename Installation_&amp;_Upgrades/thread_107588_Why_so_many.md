---
title: "Why so many?"
date: 2005-12-23
forum: Installation &amp; Upgrades
---

### Post by theb on 2005-12-23
I have one hdd and with partitions booting into Ubuntu and XP.
When I boot it up and it goes to the grub, how come so many Ubuntu vers come up?

I get these:

Ubuntu, kernel 2.6.12-10-386
Ubuntu, kernel 2.6.12-10-386 (recovery mode)
Ubuntu, kernel 2.6.12-9-386
Ubuntu, memtest86+

then my XP partition.

Do I need all of those and if I don't can I just delete them?

---

### Post by DevilsAdvocate on 2005-12-23
The top kernel is the one that you normally boot into.

The 2nd one down is a "recovery" kernel.  It's good to keep around if your setup gets borked.  It's a stripped down command line version though.

The 3rd one down you can delete (it's the oler version of your kernel) but you don't have to.  

The 4th one is self explanatory, also good to have around if things start acting up.

You can delete XP.

Depending on your PC, their may be other kernels that would be better for you.  If you have a PIV, try the 686 kernel.  If you have hyperthreading, add SMP.  You can install as many kernel's as your heart desires.

---

### Post by tseliot on 2005-12-23
Open Synaptic, press the "Search" button and type "linux".
A list will show up
find "linux-image-2.6.12-9-386", right click on it and select "Mark for Complete Removal" (it might ask you to remove other things, such as the restricted modules for that kernel which you don't need)
Click on the "Apply" button
And you won't see that kernel any more.

Oh, and of course you can also remove WinXP :p

---

### Post by theb on 2005-12-23
thanks for the replies,

Whats PIV?  Also, my processor is a pentium M so I'm guessing the i686 would more more correct for me?  Does it matter?  Everything seems to work fine as of right now though.

---

### Post by DevilsAdvocate on 2005-12-23
That't the beauty of this system.  You can install the 686 kernel (and you'll have an option in GRUB to use it) and if it doesn't work, boot into the other kernel.

---

### Post by AmboyGuy on 2005-12-23
PIV = Pentium 4  ( hyperthreading = emulating 2 processor cores --- i686 SMP is for multiple processors )
Pentium M = Pentium 3 class processor --- i686 works fine.
i386 kernels oddly enough will work on i386, i486, pentium, pentium 2, pentium 3, pentium 4, AMD

---

