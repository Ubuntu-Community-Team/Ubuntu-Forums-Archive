---
title: "[SOLVED] Grub/Bootloader, please help"
date: 2008-07-23
forum: General Help
---

### Post by amarkitanis on 2008-07-23
I installed Windows Vista on a 2nd partition after having initially installed Ubuntu 8.04 on the same machine.

I used this EasyBCD program and used Neogrub so i could boot on linux after vista scorched the bootloader. After successfully booting into linux, I re-installed grub and the original boot screen was back in place.  I then removed the neogrub.

What i never encountered before though, is when I press enter to boot into vista, it shows some text, can't say much about it though as it runs quite fast, I 've never encountered before. Is that normal? although it doesn't cause any problems i'd like to remove it if possible. Has this got anything to do with vista scorching the bootloader? or the EasyBCD program?

Please help.

P.S if there's any way I can provide you with a screenshot please do so, but i'm not sure how i could get a screenshot at that time. maybe take a quick digital photo.

Thanks for your time.

---

### Post by justleen on 2008-07-23
could it be the windows boot menu you are seeing? 
open up c:\boot.ini, check if there is a delay there. .should be 0

---

### Post by amarkitanis on 2008-07-23
i managed to fix the system by myself... all i had to do was delete the grldr file. everything appears to be workin just fine :)

---

