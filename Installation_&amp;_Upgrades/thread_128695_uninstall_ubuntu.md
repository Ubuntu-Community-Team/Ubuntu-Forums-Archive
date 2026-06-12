---
title: "uninstall ubuntu"
date: 2006-02-12
forum: Installation &amp; Upgrades
---

### Post by lulemurfan on 2006-02-12
Would it be possible to uninstall ubuntu from my computer if i don't like it?

---

### Post by lloydkirk on 2006-02-12
Sure, just delete the ubuntu partition.

---

### Post by Herman on 2006-02-12
Yes, that's half right, you do delete the Ubuntu partition.
The other half of it is then you need to get your MBR to point to Windows again when your computer is booting up.

When you install GRUB to MBR during the Ubuntu installation it makes the MBR point to Ubuntu. Most of GRUB's working parts are in your Ubuntu partition. If you delete the Ubuntu partition you will also be deleting the parts of GRUB that you need to point back to Windows again to boot Windows.

Either before or right after your delete your Ubuntu partition you will need to change your MBR back to the way it used to be before you installed Ubuntu, which means it will just point right to Windows. If you don't you will just end up with a black screen and an error message when you try to boot up.

Try what it says in [this link]("http://users.bigpond.net.au/hermanzone/p18.htm").

---

### Post by lloydkirk on 2006-02-12
He never specified what boot loader he was using or if in fact he intended to install it to the MBR. ..

---

