---
title: "Updated Linux, now can't get past memtest"
date: 2009-08-02
forum: Installation &amp; Upgrades
---

### Post by crybllrd on 2009-08-02
I updated my aunts Linux Ubuntu. It hasn't been updated in many years, if ever.
After dowloading and instaling all the updates, it automatically restarted.
When it restarted, it went to memtest86. I figured I would just let it finish, but it went for days.
I can't get through memtest to the desktop.
What went wrong, and how can I fix it?

---

### Post by Chemical Imbalance on 2009-08-02
I believe memtest runs indefinitely until you stop it.

---

### Post by crybllrd on 2009-08-02
How to I just get back to the desktop? 
When I boot it goes straight to memtest, with the option of pushing ESC to get a menu.

---

### Post by Chemical Imbalance on 2009-08-02
> **crybllrd said:**
> How to I just get back to the desktop? 
When I boot it goes straight to memtest, with the option of pushing ESC to get a menu.

Press ESC to enter the GRUB menu to choose which kernel you want to boot.

---

### Post by izizzle on 2009-08-02
Press Escape then?

---

### Post by crybllrd on 2009-08-02
All I have is:
 
root (hd0,0)
kernel /boot/memtest86+.bin
quiet
 
I guess this is my problem. Where do I need to ad a line, and what do I need to add?
Thanks

---

### Post by dagrump on 2009-08-02
Just back up her home folder & install a more current version. There have more than likely advances made that warrant the update. I would just go with 8.04.3?? I'm thinking that is the latest LTS. If not I'm sure I'll hear about it.
I guess this critter doesn't get a lot of use?

---

### Post by Chemical Imbalance on 2009-08-02
Try booting the first one (root), then if that doesn't work try "quiet".

If neither of those work you can boot a liveCD and restore GRUB.

But I agree with OP, you should think about installing a newer version of Ubuntu if it has been years since you last did.  Of course backup all her files no matter the case (again, you can do this with a liveCD).

---

