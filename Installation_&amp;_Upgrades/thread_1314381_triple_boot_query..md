---
title: "triple boot query."
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by marbor on 2009-11-04
hi guys!

Rightho, i want to install the latest ubuntu onto a formatted drive(ntfs). i also have windows xp32 on another drive, and x64 on yet another drive. all on the same pc. what i want to know is how this would affect the MBR. will ubuntu detect the other OS's, and adjust the MBR accordingly, or is there some other tomfoolery i have to get up to to access windows again?

cheers,

mark.

---

### Post by cariboo on 2009-11-04
Ubuntu 9.10 uses grub2, it may not detect your other installation at the start, but all you have to do to have them in the menu is ti open and Applications-->Accessories-->Terminal and type:

```
sudo update-grub2
```

This will detect al the OSes on your computer.

---

### Post by marbor on 2009-11-04
Sweet as mate, Thanks. Now to go haulin' files around everywhere ): !

---

### Post by Mark Phelps on 2009-11-04
> **marbor said:**
> hi guys!

Rightho, i want to install the latest ubuntu onto a formatted drive(ntfs).

You can't install Ubuntu to an NTFS-formatted drive, unless you install inside MS Windows using Wubi -- and folks are reporting lots of problems getting Wubi to work under 9.10.

Your best bet would be to use the Ubuntu LiveCD to remove the NTFS partition from that drive, and when you install Ubuntu to it, choose the "Use entire drive" option to allow it to create and format the necessary partitions.

>  what i want to know is how this would affect the MBR. will ubuntu detect the other OS's, and adjust the MBR accordingly, or is there some other tomfoolery i have to get up to to access windows again?

It will overwrite the MBR -- but you already have a post above that tells you how to update GRUB to include them.

---

