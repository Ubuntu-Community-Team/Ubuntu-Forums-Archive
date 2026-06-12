---
title: "dual-boot question"
date: 2006-02-06
forum: Installation &amp; Upgrades
---

### Post by dannyliu on 2006-02-06
I have a dell 4550 machine which has two hard drives. One is Ubundu (master) and the other is Windows XP (slave). I create a grub loader on Ubundu and add the load section for Windows XP.

Based on comments in this forum, I can successfully boot two OSs using the grub menu.

Here is the parameters I used in menu.lst.

map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
makeactive
chainloader +1

The logic behind is that the OS can only boot from the master drive and the hard drive of Ubundu and XP should be switched during this process.

I am wondering why the following parameter does not work.
rootnoverity (hd0,0)

Cause it sounds reasonable after the mappings.

Thanks.
Dan

---

