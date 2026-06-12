---
title: "Screen resolution problem"
date: 2006-12-02
forum: Hardware &amp; Laptops
---

### Post by oli888 on 2006-12-02
Thanks for reading my problem. I'm having it on most Linux distributions I try. I like Ubuntu, but am unable to use it because of this issue.

The terminal is fine, but when I load anything graphical e.g. GNOME, the screen is not aligned correctly. For example, if the screen is meant to load:

0123456789
0123456789
0123456789
0123456789
0123456789
0123456789
0123456789
0123456789
0123456789
0123456789

It instead comes up with:

__________
__________
__________
__________
__________
789____123
789____123
789____123
789____123
789____123

where _ is just black.

Is there a way to get this working again? It would really be appreciated.

Oli

---

### Post by teaker1s on 2006-12-02
what make is your graphics?

---

### Post by oli888 on 2006-12-03
Thanks for the reply.

Triden Video Accelerator Cyberblade.

---

### Post by teaker1s on 2006-12-03
try googling
Triden Video Accelerator Cyberblade linux 
or
Triden Video Accelerator Cyberblade linux

to see  if you can find anyone who has same product.
Do you know if it's a triden chip on the graphics card or maybe intel or nvidia?

also you can try

'sudo dpkg-reconfigure xserver-xorg' and try 'vesa' as the driver and if you find out the technical spec of your display you can enter them in and it may correct the problem.

---

