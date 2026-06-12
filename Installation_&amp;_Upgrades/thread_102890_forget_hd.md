---
title: "forget hd ???"
date: 2005-12-13
forum: Installation &amp; Upgrades
---

### Post by Anakroyd on 2005-12-13
HI to all, i'm new on this forum, for the first time I installed ubuntu on my old pc at work (p166,256k ram, 4gb hd) everything seems all right and at the end a pop up windows tell me : succesfull installation, but.......

..... when I restarted the pc I saw this:
          NO SYSTEM DISK PLEASE INSERT BOOT DISK AND PRESS ENTER


  Argh !



Of course i took a look to bios setting, i tried to insert again the cd etc etc  but i had no results, .... can you help me ???

PS: I do not install again linux 'couse installation seem good and it's a bit slow on this machine (one hour and half )   8((((((

---

### Post by matthewv on 2005-12-13
It sounds like grub didn't install. Try booting the install cd, and choosing the option to enter a recovery console. Once at a root console, type ```
grub-install /dev/hda
```

Hope that works:)

---

### Post by Anakroyd on 2005-12-13
no, there is a trouble on disk cable now it seems ok but i have another trouble :(

---

