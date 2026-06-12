---
title: "Expresscard question"
date: 2010-01-12
forum: Hardware
---

### Post by gmay00 on 2010-01-12
I have 9.10 and just got a cheapo eSATA expresscard which works great when plugged in before booting. Is there any way to make the expresscard hot swappable though? 
Thanks a lot..

---

### Post by slalomchip on 2010-05-26
Can't help you on the hot swappable part, but maybe you can help me.

Which cheapo esata expresscard did you get and where did you find the drivers?

UPDATE - UPDATE - UPDATE - forget the question - I got my IOGear GPS702e3 working by changing the line 

*GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"*

to 

*GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pciehp.pciehp_force=1"*

in the file 
[I]
/etc/default/grub[/I]

---

