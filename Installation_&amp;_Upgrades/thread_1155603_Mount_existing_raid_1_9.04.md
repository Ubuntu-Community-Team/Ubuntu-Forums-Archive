---
title: "Mount existing raid 1 9.04"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by rsdunker on 2009-05-11
I recently switched an opensuse box over to ubuntu 9.04.  I had a software raid 1 on the old machine and cannot figure out how to reassemble and mount it on my new Ubuntu install.

fdisk shows both partitions listed as linux raid autodetect.

Been at this awhile and I'm really getting stumped.  Plus, I'm a bit scared to just try stuff out because I would prefer to keep my data intact.  Thanks for any help or nudges in the right direction.

---

### Post by orange-wedge on 2009-05-11
i've never setup a software raid array personally, but i did do some research on it back when i was going to set up an array for a box at work.  unfortunately we ended up using the old windows drive...

but i would take a look at the command mdadm.  you may need to install the package:
[html]sudo apt-get install mdadm[/html]there are tons of how-tos on the web for recovering raid arrays... i would suggest searching first.

---

