---
title: "Intriguing / Bizarre Boot Issue"
date: 2005-06-23
forum: Hardware &amp; Laptops
---

### Post by neurosion on 2005-06-23
In short, I can only boot into my 32-bit Ubuntu if I boot into any other operating system first.

It's just about the strangest issue I've ever had.  If I cold boot into my 32-bit Ubuntu, it runs through the text for the startup process, blanks out the screen, and where  I'd usually see the NVIDIA logo, I get nothing.  And none of the usual tricks (CTRL-ALT-F1, adding VGA=791 to the boot, etc.) do any good.

However, if I cold boot into EITHER my 64-bit Ubuntu or (get this) Windows XP, and then reboot, I can boot into my 32-bit Ubuntu without a hitch.

Does this behavior surprise anyone else?  Any ideas?

Since I never considered that state could persist through a reboot, I'm perplexed.  Incidentally, I have confirmed that this only happens when I'm using the nvidia accelerated drivers; when I reconfigure for nv everything works fine.  All in all, though, this strikes me as some funky voodoo.

Specs:

Athlon64 939 on Asus A8V
NVIDIA GF6800GT Ultra
1GB RAM
etc. available upon request

---

