---
title: "Grub, and Windows"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by nlakes on 2009-05-07
Hi everyone. 

I've got a question about grub and Ubuntu, I think I may have an issue - but I'm not entirely sure because I'm not the most tech savvy person. 

At the moment I dual-boot Ubuntu 9.04 and Vista. 
I am downloading Windows 7 RC and want to install it over Vista. But will grub realise that Vista is gone and Win7 has taken its place? or do I manually need to update grub?

Secondly, will grub even appear if I install win7? In the past windows has just decided it wants to load itself automatically. 

Thank!

---

### Post by HyRax on 2009-05-07
If you install Windows 7 over the top of Vista, it will destroy the bootloader and prevent Ubuntu from starting (because Windows 7 doesn't care for any other non-Windows OS's - in fact, it would break the EULA if it did).

But this is OK. You can fire up an Ubuntu LiveCD and re-install the GRUB bootloader without needing to reinstall Ubuntu which will restore your dual-boot capability.

There's loads of guides out there on how to do this - just Google up "reinstall GRUB".

---

### Post by nlakes on 2009-05-08
Thanks for that, I've found some instructions on how to do that.

---

