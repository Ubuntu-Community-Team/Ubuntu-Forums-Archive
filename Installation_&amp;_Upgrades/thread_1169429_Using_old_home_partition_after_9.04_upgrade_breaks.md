---
title: "Using old home partition after 9.04 upgrade breaks internet"
date: 2009-05-25
forum: Installation &amp; Upgrades
---

### Post by conjunctivitis on 2009-05-25
hi.

i have an acer extensa 4420 laptop, with amd athlon 64 x2
and broadcom integrated wireless.

i have a seperate ext2 home partition which i use to share music and documents with vista and recently formatted my 8.10 root and did a clean install of 9.04.  when i started up 9.04 (with the default /home partition) my internet connections worked fine.  i edited the fstab to point to my home *partition* from 8.10 and after rebooting, neither wireless nor lan connections are detected, and my wireless indicator light doesn't light up.


i returned to the default fstab, so i'm now using a default ubuntu 9.04 installation with the default /home directory to write this.  i assume the configuration of my wireless hardware is stored in a few files in the /home directory of my fresh installation.  could i just copy those into the old /home partition to fix wireless and go from there?

thanks

---

### Post by conjunctivitis on 2009-05-26
bump

---

