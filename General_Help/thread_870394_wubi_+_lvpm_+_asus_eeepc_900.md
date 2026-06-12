---
title: "wubi + lvpm + asus eeepc 900"
date: 2008-07-25
forum: General Help
---

### Post by suoko on 2008-07-25
i've installed wubi and then moved it to sda1 with lvpm
now grub starts but can't find kernel

error 17: cannot mount selected partition
press any key to continue

grub line is
root ()/ubuntu/disks

tried changing it to
root /dev/sda1
with no success
any tips ^?

---

### Post by Manacit on 2008-07-26
try "root (hd0,0)"

---

### Post by suoko on 2008-07-26
> **Manacit said:**
> try "root (hd0,0)"

thanks a lot.
that worked

---

