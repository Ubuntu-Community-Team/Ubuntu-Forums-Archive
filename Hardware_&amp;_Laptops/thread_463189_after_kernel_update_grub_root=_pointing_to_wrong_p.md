---
title: "after kernel update grub root= pointing to wrong partition, still boots okey"
date: 2007-06-03
forum: Hardware &amp; Laptops
---

### Post by hardyn on 2007-06-03
after the update, i noticed that when booting, the kernel is trying to restore from hd(3,3), i don't have a disk 3, or 2, or 1?

the root=hd(0,3) line is pointing to my swap?
my root partition is hd(0,4)

it still boots okey... should i correct the root= line?

help

---

### Post by merlinus on 2007-06-03
I would, to forestall any future difficulties.  You might also want to check the entries in

/boot/grub/menu.lst

-merlin

---

### Post by philcaetano on 2007-10-01
I've done 2-3 updates and everytime the grub gets updated, it will set the wrong partition / Drive on my pc too!  I have 3 drives and it keeps putting the menu entry to (hd2,1) instead of (hd0,1).  The only issue I see is that  I have 2 Satas and 1 ide drive...  Seems "Grub" sees Sata drives first but in Ubuntu, it seems teh IDE drive first!.

I have no problem fixing the menu after each upgrade.  But This might be a bug that should be looked into?

---

### Post by hums07 on 2007-10-21
I installed a friend's laptop with Feisty on an external HD. His internal HD was broken burying Vista with it. For some reasons he does not want to open his laptop or call an engineer for repair so Ubuntu is an alternative.

Using liveCD, internal HD was detected but unusable. Install was successful, but It needs the internal HD disabled before Grub work. Also in menu.lst, root needs to be changed to point to (hd0,5), original value was (hd1,5) and hd0 originally pointed to internal HD.

When the system update, the menu entry is automatically changed back to (hd1,5). It happened again when it was upgraded to Gutsy. My friend is computer illiterate, so he relies on me to correct the grub menu. I wish I could tell him what to do next time he encountered this, but he might be too scared.

In this case I feel there is something that could be "corrected".

---

