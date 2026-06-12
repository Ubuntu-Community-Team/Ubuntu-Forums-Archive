---
title: "Triple boot - uninstall 3rd distro"
date: 2009-02-06
forum: Installation &amp; Upgrades
---

### Post by fhsm on 2009-02-06
I'm triple booting right now (XP, Ubuntu & Mint).  I put Ubuntu and Mint on at more or less the same time to see which I liked more.  I've found myself using Ubuntu exclusively so I'd like to take back the space from mint and add it to ubuntu.

How do I do this?  Should I just expand the Ubuntu partition into mint?  What about Grub?

Thanks.

---

### Post by [pl]ice on 2009-02-06
I have the a similar problem, normaly you have to only edit /boot/grub/menu.list (make backup...) then add the another system there and partition :/
good luck :)

---

### Post by Tim Sharitt on 2009-02-06
You can expand the Ubuntu partition with gparted from the live cd, or  erase or reformat the mint partition for additional storage.

Is grub installed on the Ubuntu or Mint partition? If it is installed on the Ubuntu partition, you can simply remove the Mint entry from menu.lst.

---

### Post by fhsm on 2009-02-08
I don't know where grub is installed.  How can I find out?

I don't know if this is helpful:
```

/dev/sda1 ntfs IBM_PRELOAD
/dev/sda3 extended
    /dev/sda5 (this is mint)
    /dev/sda7 (this is ubuntu)
    /dev/sda6 linux-swap

```

---

### Post by fhsm on 2009-02-10
> **Tim Sharitt said:**
> You can expand the Ubuntu partition with gparted from the live cd, or  erase or reformat the mint partition for additional storage.

Is grub installed on the Ubuntu or Mint partition? If it is installed on the Ubuntu partition, you can simply remove the Mint entry from menu.lst.

Thanks for this bit of advice.  I've used the [boot info bash script](http://sourceforge.net/projects/bootinfoscript/) to find that grub is installed on ubuntu.  I suspected this because I installed ubuntu after I installed mint and because that's the menu.lst file that I edit.

If I use gparted on a live CD and expand ubuntu out over mint then my mint partition will have been effectively deleted.  Will deleting that partition keep me from booting back into ubuntu?  I'm wondering if the partitions will get renumbered or something.

---

