---
title: "How to change video card for display?"
date: 2005-05-22
forum: Hardware &amp; Laptops
---

### Post by weenhound on 2005-05-22
Hey guys,

I've just installed Ubuntu and am loving it so far!!!  

I've just got one problem and that is that Ubuntu has configued the wrong video card to display X through.

I have two video cards in my system.  An AGP card and a PCI card.  I would like to use the AGP card for display.

My system boots up displaying all the system checks on the AGP card but when X loads it sends the signal to the PCI card.  How can I change it so that the signal is only sent to the AGP card???  I have tried taking the PCI card out but X won't load without it.

Thanks in advance!

---

### Post by matej on 2005-05-23
[QUOTE=weenhound]
I have two video cards in my system.  An AGP card and a PCI card.  I would like to use the AGP card for display.
[/QUOTE]
You should reconfigure x.org to use your agp card.
 ```
sudo xorgconfig
```

---

