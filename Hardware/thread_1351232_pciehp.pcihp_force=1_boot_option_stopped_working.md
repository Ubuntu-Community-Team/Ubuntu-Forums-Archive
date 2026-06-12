---
title: "pciehp.pcihp_force=1 boot option stopped working"
date: 2009-12-10
forum: Hardware
---

### Post by darkshadow on 2009-12-10
I have a card reader in my laptop that requires that to work and it used to but just today I noticed it stopped working.

I have not had a need to use the card reader in a couple weeks and there has been kernel update so I am blaming them.

Does anyone have a fix since without it I can only use the card reader if a card is inserted at boot time which is a problem for me.

I have checked dmesg and I am still booting with the option.

---

### Post by darkshadow on 2009-12-10
I just re-read my title and noticed a spelling mistake it is supposed to be pciehp.pciehp_force=1 I am even more confused since I copy and pasted it from /etc/default/grub a file I have not edited since it was working so what could of modified it without me knowing.

Probably the update to Grub that I let happen in update-manager yesterday.

Oh well it is fixed now and everything is working. Did anyone else have a problem with the recent Grub update modifying the config file?

---

