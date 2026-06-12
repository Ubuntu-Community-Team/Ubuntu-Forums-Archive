---
title: "Ubuntu update breaks Grub and dual boot"
date: 2009-02-20
forum: Installation &amp; Upgrades
---

### Post by kevin_405 on 2009-02-20
I have Ubuntu 8.1 setup on my m/c as a dual boot with Grub as the boot manager.. Did a upgrate yesterday and today i cannot see the Win XP part of the menu.

I did get a popup for updating the menu.lst , not knowing what it was i chose overwrite option and i guess that broke my dual boot..

Does the update manger keep a backup of the old menu.lst that i can use to superseed the update..

Any suggestions to recover the dual boot..

---

### Post by taurus on 2009-02-20
Look in /boot/grub to see if there is a backup version.

Applications -> Accessories -> Terminal
```
ls -la /boot/grub
```

---

