---
title: "HP LaserJet Print Driver problems"
date: 2007-05-08
forum: Hardware &amp; Laptops
---

### Post by jettplane on 2007-05-08
I have an HP LaserJet 4 printer on a Windows network.  No trouble printing EXCEPT that I can't get the tray options to work. I've tried all the included drivers, no luck.   They work fine in Windows.

Second question, related.  There is no option for first page letterhead, second page plain paper.  I understand that a foomatic command can do this:

$ foomatic-rip -P foo1 -o 1:InputSlot=LowerTray -o InputSlot=LargeCapacity

but I don't know how to put that in the PPD.

Thanks-

---

### Post by bmc3 on 2007-06-21
Hello!

I don't know how to incorporate the "first page head, other pages white" into the CUPS system. But I think it is necessary to write some sort of filter which inserts the right commands into the .PS file.

I really would like to set up a second (virtual) printer that always prints this way while the "real" printer just uses the default tray for all pages.

I couldn't find any clues in the cups documentation. :-(

bye

---

