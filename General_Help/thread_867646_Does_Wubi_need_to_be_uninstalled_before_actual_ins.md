---
title: "Does Wubi need to be uninstalled before actual install?"
date: 2008-07-23
forum: General Help
---

### Post by Helical on 2008-07-23
I ask because I can't currently access my Windows partition due to an automatic Windows Update. Will it be a problem if there are two Ubuntu's on the GRUB?

Thanks.

---

### Post by overdrank on 2008-07-23
Moved :)

---

### Post by ago on 2008-07-23
No problem, wubi is anyway on the windows bootloader, so if you install grub before that you will have 2 boot menus. Grub first with an option "Ubuntu" (full installation), or "Windows" and inside that you will have a second boot menu with options "Windows" and "Ubuntu" (wubi).

Of course once you install to a real partition you can migrate the settings and then uninstall wubi.

---

