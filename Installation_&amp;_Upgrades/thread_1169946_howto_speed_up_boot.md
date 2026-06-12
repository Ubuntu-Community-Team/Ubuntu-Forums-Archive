---
title: "howto speed up boot"
date: 2009-05-25
forum: Installation &amp; Upgrades
---

### Post by keratos on 2009-05-25
one method to speedup boot, amongst others, is to simply remove the linux kernel interrogation of specific BIOS drive queries, which, in reality are not required on most systems.

add **edd=disable** to the **kernel** line in /boot/grub/menu.lst , e.g:

```

title ubuntu 9.04
kernel ...  **edd=disable**
initrd ...

```

---

