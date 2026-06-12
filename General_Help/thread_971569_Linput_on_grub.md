---
title: "Linput on grub"
date: 2008-11-05
forum: General Help
---

### Post by The Judderman on 2008-11-05
Dear all,

I've recently reinstalled ubuntu on my laptop, and I'm glad to be back! I also wanted to try out linpus, with its 16 sec boot time, just for fun. I installed it after my ubuntu install (I also have vista) and it wiped my grub, so that I could only boot into linpus (which was fun, because it is quick!)

I repaired my grub menu, and put it back to (hd0) (which might have been a mistake), and got my ubuntu/windows grub menu back, but I can't boot back into linpus.

Any ideas of how to put it back on my grub menu and boot into it?

Thanks!

---

### Post by The Judderman on 2008-11-09
Just for interest, here is how I solved this simple problem. I found the grub file on the linput partition, copied the entry for the Linpus and pasted it into the /boot/grub/menu.lst file in Ubuntu, and I now have a menu giving me the option to boot into Ubuntu, Linpus or Windows. 

This means that I can have lots of fun!!!

Thanks!

---

