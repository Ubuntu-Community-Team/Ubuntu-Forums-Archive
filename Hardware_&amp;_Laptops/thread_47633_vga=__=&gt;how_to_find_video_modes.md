---
title: "vga= ? =&gt;how to find video modes"
date: 2005-07-09
forum: Hardware &amp; Laptops
---

### Post by Sav on 2005-07-09
Hi, my laptop video chipset is an i855gm.
I recompiled the latest 2.6.12 kernel (from breezy) with the intelfb flag.
With vga=792 the system boots, but how can I set the proper resolution: 1280x800?
Thanks

---

### Post by marb on 2005-07-09
here's a nice overview of vga-modes:
[link](http://www.antlinux.com/pmwiki/pmwiki.php?n=HowTos.VgaModes) 

i solved my resolution problem this way: probably it works the same way with your machine. in /boot/grub/menu.lst:

video=radeonfb:1400x1050 vga=0x342

---

### Post by Sav on 2005-07-10
[QUOTE=marb]here's a nice overview of vga-modes:
[link](http://www.antlinux.com/pmwiki/pmwiki.php?n=HowTos.VgaModes) 

i solved my resolution problem this way: probably it works the same way with your machine. in /boot/grub/menu.lst:

video=radeonfb:1400x1050 vga=0x342[/QUOTE]

Thanks, but 1280x800 is not listed.
How did you discover the vga parameter for your resolution?

---

### Post by marb on 2005-07-11
[QUOTE=Sav]How did you discover the vga parameter for your resolution?[/QUOTE]
I did a search on Google-Groups: "t41p vga=" (I have a IBM T41p)

---

### Post by Sav on 2005-07-11
[QUOTE=marb]I did a search on Google-Groups: "t41p vga=" (I have a IBM T41p)[/QUOTE]

Thanks, but I wasn't luky enough  ](*,)

---

