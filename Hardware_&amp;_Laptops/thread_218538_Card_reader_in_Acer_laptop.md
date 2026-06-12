---
title: "Card reader in Acer laptop?"
date: 2006-07-18
forum: Hardware &amp; Laptops
---

### Post by MarinaraOfDeath on 2006-07-18
I've got an Acer Aspire 1691WLMi (the one CompUSA carried, which seems to be a bit different from the one available in Europe). Most everything works flawlessly, but one of the last, and most critical things, it that the 4-in-1 card reader doesn't exist. lspci doesn't see it, there's no mount point anywhere in the file system, etc. 

1) Other threads indicate this is heavily chipset-dependent. How do I tell which reader I've got?

2) Is there a hardware compatability list somewhere with the list of readers known to work and/or known to not work?

3) Has anyone else gotten a card reader in an Acer working?

---

### Post by ThrobbingBrain66 on 2006-07-19
I've read on the forums that card reader support is almost non-existant on the current kernel (2.6.15) but does exist, atleast in an experimental mode, on the 2.6.17 kernel.  The card reader on my Toshiba doesn't work either.  Someone else may be able to tell you for sure...

But if you're feeling adventurous, you could always try to compile a custom kernel.  There are a couple of howtos floating around in the forums.

---

