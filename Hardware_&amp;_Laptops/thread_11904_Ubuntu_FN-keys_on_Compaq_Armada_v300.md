---
title: "Ubuntu FN-keys on Compaq Armada v300"
date: 2005-01-20
forum: Hardware &amp; Laptops
---

### Post by Sasayaki on 2005-01-20
Hey guys, it's me again.

I got Ubuntu installed on my laptop (a Compaq Armada v300), but I'm having trouble with the FN keys. Those are the keys which, when in Windows, I press the 'FN' key with an F key (IE F12), then it dims the brightness or whatever.

How can I get them working in Ubuntu? The screen is too bright (it washes out the colours and is probably damaging it) but I can't turn it down... they keys don't work!

Help?  :???:

---

### Post by Sasayaki on 2005-01-20
... anyone?

---

### Post by Sasayaki on 2005-01-21
Ok, fixed it- had to edit /boot/grub/menu.lst and add acpi=force to the kernel options. Then, holding fn-F9, I use the up and down arrows to adust the brightness, contrast, sound, etc.

---

