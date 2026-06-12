---
title: "replace motherboard, reinstall Ubuntu?"
date: 2006-10-25
forum: Hardware &amp; Laptops
---

### Post by DFreeze on 2006-10-25
My motherboard just died on me. I'm going to replace it (probably AsRock k7nf2), but I'm curious as to whether I have to reinstall Ubuntu? Or does a simple 'sync hardware - remove unused modules' kind of instruction suffice?

---

### Post by nocturn on 2006-10-25
> **DFreeze said:**
> My motherboard just died on me. I'm going to replace it (probably AsRock k7nf2), but I'm curious as to whether I have to reinstall Ubuntu? Or does a simple 'sync hardware - remove unused modules' kind of instruction suffice?

No need to reinstall.  Your system should boot fine on the new board.

You might need to adjust the staticly loaded modules, but that's all.

---

### Post by az on 2006-10-25
You probably will have to reconfigure your video card, as that is only configured when the xserver-xorg package is instaled - it is not autodetected upon every boot.


BOot into recovery mode the first time and run

dpkg-reconfigure -phig xserver-xorg

and then run 

init 2

to get into desktop mode.

All the other stuff is autodetected, unless you change your hard drive order.

---

### Post by DFreeze on 2006-10-25
Thanks, I'll do just that, as soon as I receive the board. I'll come back here with the results.

---

### Post by DFreeze on 2006-11-07
I replaced the board and I didn't even have to reconfigure the videocard. It booted up fine, even nVidia needed no reinstall!

However, the board does something I've never seen before. I started a new thread about it, because it's not software (Ubuntu) related, but more of a hardware quirckyness. I'd appreciate it if you read it and gave your thoughts on the matter.

[link]("http://ubuntuforums.org/showthread.php?t=294100")

---

