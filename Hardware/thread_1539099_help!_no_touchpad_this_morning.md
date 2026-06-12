---
title: "help! no touchpad this morning"
date: 2010-07-26
forum: Hardware
---

### Post by koda on 2010-07-26
Hello,
i have a vaio vpcz1 with multitouch touchpad.
It worked great until today, now it doesn't work at all and my xinitrc fails with

unable to find device SynPS/2 Synaptics TouchPad

i don't really know how this has happened, can anyone help me?
Koda

---

### Post by koda on 2010-07-26
the grub update was the culprit
i reset i8042.nopnp in the kernel line and everything started working

---

