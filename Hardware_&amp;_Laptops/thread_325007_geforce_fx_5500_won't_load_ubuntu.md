---
title: "geforce fx 5500 won't load ubuntu"
date: 2006-12-24
forum: Hardware &amp; Laptops
---

### Post by trav1085 on 2006-12-24
I tried to load Ubuntu 6.10 on my Dell Dimension 1100 with my new nVidia GeForce FX 5500 256MB PCI (not pcie). Everything would go alright until It tried to load x, and a ugly looking dialog said that X server could not be loaded and if I want to view the log file. I chose no and after that it said something about starting GDM. THen it brings it to a terminal screen with mount and fsck commands that are on there.

I'm wondering why it doesn't work with that. I thought linux was compatable with any card

---

### Post by taurus on 2006-12-24
Boot into recovery mode from GRUB menu and at the prompt, reconfigure your X again...

```
dpkg-reconfigure xserver-xorg
startx
```

---

### Post by po0f on 2006-12-25
trav1085,

Maybe [this link](http://doc.gwos.org/index.php/Nvidia_Intel_Integrated) will help you, it got mine working.

---

### Post by rengard on 2008-04-05
that link does not work.....

---

### Post by chrislovessushi on 2008-05-14
having the same issues...tried a lot of different solutions as well...

---

