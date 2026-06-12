---
title: "dell latitude C610 crashes"
date: 2005-01-05
forum: Hardware &amp; Laptops
---

### Post by existentialmutt on 2005-01-05
I just installed Warty on my Dell Latitude C610.  Everything went pretty much OK, the install went through without a hitch, but now the computer hangs if I plug in the network cable or the power cable after boot time.  We're talking total lockup- no mouse, no keyboard, no switching virtual terminals, nothing.  Afterwards, I don't notice anything out of the ordinary in syslog or messages.  I just apt-getted linux-image-2.6.8.1-4-686 which seems to have fixed the issue for the network cable but it continues to freeze whenever I plug in the power cable.

Are these the warts that were spoken of in the reviews I read?  Any suggestions would be most appreciated.

---

### Post by existentialmutt on 2005-01-19
Ha!  Fixed it!

added the following to my kernel line in grub:

noapic nolapic

---

