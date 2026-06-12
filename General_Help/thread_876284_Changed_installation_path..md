---
title: "Changed installation path."
date: 2008-07-31
forum: General Help
---

### Post by Panda X on 2008-07-31
Hello. I installed Wubi today and proceeded to changed the install path from X:\ubuntu to X:\Operating Systems\Ubuntu

I changed the entry in the BCD Store to load to the new path, (\Operating Systems\Ubuntu\winboot\wubildr.mbr) but when I try to boot into to it I just get this GRUB4DOS screen and it doesn't do anything.

Is there something else I need to change?

---

### Post by ago on 2008-08-01
> **Panda X said:**
> Hello. I installed Wubi today and proceeded to changed the install path from X:\ubuntu to X:\Operating Systems\Ubuntu

I changed the entry in the BCD Store to load to the new path, (\Operating Systems\Ubuntu\winboot\wubildr.mbr) but when I try to boot into to it I just get this GRUB4DOS screen and it doesn't do anything.

Is there something else I need to change?

white spaces are not allowed in the path. you also need to change ubuntu/disks/boot/grub/menu.lst and winboot/menu.lst and then copy the latter to c:\

---

