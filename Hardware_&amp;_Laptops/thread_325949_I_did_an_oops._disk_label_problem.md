---
title: "I did an oops. disk label problem"
date: 2006-12-26
forum: Hardware &amp; Laptops
---

### Post by kolinab on 2006-12-26
Hi all,

I've been happy diddling and was trying to change the label of my external usb disk, and accidentally performed the following comand:

sudo e2label /dev/sda1 Brick

What I meant to do was name my usb backup drive "Brick" (don't laugh) but I hope I didn't screw up my root partition. Does anyone know the default label of /dev/sda1 (my root)? I'd feel better if I put it back the way it was before.

Thanks!

K

---

### Post by kidders on 2006-12-26
Hi there,

Ordinarily, you can call any filesystem anything you want. Your original label (assuming you even had one) doesn't matter :-)

... unless of course you were using it to identify the the filesystem, in which case, I imagine you'd know it.

No need to worry!

---

### Post by kolinab on 2006-12-26
(sigh) That's good. Now the label is root. I ought to be careful running sudo commands. Thanks!

---

