---
title: "Can't get Ubuntu to work on my Thinkpad 600x! Anybody??"
date: 2005-09-28
forum: Hardware &amp; Laptops
---

### Post by greenway on 2005-09-28
Installation goes fine, no problem what so ever. After entering my username and password combination, the fun is over! Just a dark brown screen, still able to move my mouse though...

I have tried many different graph drivers, none of them seems to does the trick. Also added the "VGA=771" at the kernel line in menu.lst, also nothing. Getting any kinda frustrated here! Any help would be very appreciated.

---

### Post by mlomker on 2005-09-28
Did you try 'vesa'?

---

### Post by scoot1212 on 2005-09-28
acpi=off pnpbios=off  add that to your grub menu for kernel options...i believe..i'll have to double check it.
good luck
scott

---

### Post by scoot1212 on 2005-09-28
xorg.conf

video driver i have "NeoMagic Corporation NM2360 [MagicMedia 256ZX]

just change the DefaultDepth to 16.

good luck
scotth

---

### Post by greenway on 2005-09-29
Thanks guys, but I already solved the problem by adding the "irqpoll" to the kernel line in the grub file.

---

### Post by scoot1212 on 2005-09-29
nice..i'm going to give irqpoll a shot on mine

---

