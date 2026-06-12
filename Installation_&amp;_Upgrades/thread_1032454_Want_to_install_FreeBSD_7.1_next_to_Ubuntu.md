---
title: "Want to install FreeBSD 7.1 next to Ubuntu"
date: 2009-01-06
forum: Installation &amp; Upgrades
---

### Post by marcelkoopman on 2009-01-06
I've got Ubuntu now, but have some space left for FreeBSD.
Can I just resize some partitions and start the installer of FreeBSD?
If grub gets deleted can I restore it from the Ubuntu cd?

---

### Post by tuxxy on 2009-01-06
> **marcelkoopman said:**
> I've got Ubuntu now, but have some space left for FreeBSD.
Can I just resize some partitions and start the installer of FreeBSD?
If I lose grub can I restore it from the Ubuntu cd?

Yes you can resize current partitions and start the FreeBSD installer on an empty partition and yes you can easily restore GRUB from the Ubuntu Live CD, heres a good [guide]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by marcelkoopman on 2009-01-06
> **tuxxy said:**
> Yes you can resize current partitions and start the FreeBSD installer on an empty partition and yes you can easily restore GRUB from the Ubuntu Live CD, heres a good [guide]("http://ubuntuforums.org/showthread.php?t=224351")

Thanks! But what do you mean by starting the installer on a empty partition? I've got a DVD, so i can just point to my empty partition right?

Thanks again for the grub howto, i've been looking for that one :D

---

### Post by logos34 on 2009-01-06
Make sure to install the BSD bootloader to the / partition and use ubuntu grub to dual boot.  In my experience the 'chainloader' entry is the only one that works:

> title Free-BSD
root (hd0,2) 
chainloader +1
boot 

replace '(hd0,2)' with whatever bsd / is

---

### Post by logos34 on 2009-01-06
[delete - duplicate post]

---

