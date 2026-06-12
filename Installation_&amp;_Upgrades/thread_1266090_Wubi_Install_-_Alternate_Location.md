---
title: "Wubi Install - Alternate Location"
date: 2009-09-14
forum: Installation &amp; Upgrades
---

### Post by Tman-Z on 2009-09-14
Is it possible to install Ubuntu 9.04, using Wubi, and have it go to a different folder? I need to place it under the C:\Program Files directory, but I don't see an option to do this within the Wubi installer.

Alternatively, can I install it to the normal location, move the folder after the installation, and modify the Windows boot.ini file to point to the new location? I think this should work, but I'd appreciate any comments.

TIA

---

### Post by Tman-Z on 2009-09-14
It seems I might have to somehow modify the wubildr files and not necessarily boot.ini.

Any comments/help?

TIA

---

### Post by Hogosha on 2009-09-14
i would use EasyBCD to point the boot loader to the correct folder after you are done.

---

### Post by Tman-Z on 2009-09-14
I should have noted that my host system is Windows XP and not Vista (which is all EasyBCD can be used for).

I guess I might not fully understand the boot.ini file and wubildr. The line in boot.ini points to the wubildr.mbr file within the \ubuntu\disks\... directory structure. If I just modify that entry to say something like \directoryx\ubunut\disks\... where directoryx is the directory I moved the ubuntu folder into, would that be enough?

TIA

---

### Post by Tman-Z on 2009-09-14
bump...

---

