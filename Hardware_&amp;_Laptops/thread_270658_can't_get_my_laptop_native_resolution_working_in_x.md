---
title: "can't get my laptop native resolution working in xubuntu"
date: 2006-10-03
forum: Hardware &amp; Laptops
---

### Post by hookjaw on 2006-10-03
Hi I just bought an old dell laptop 
model cpx d300xt
p2 300
64 mB ram
video controller is neomagic 2160 with 2mB video memory

i installed xubuntu on it and everything works fine but that i cant get my native resolution working (1024x768)i'm stuck with a blurry 800x600

im quite new to the linux world and i dont know what to look for
is it xfce that cannot see xorg settings
or does xorg handle my video memory properly
where do i go to fix the problem?

---

### Post by phileas on 2006-10-04
I am surprised that the auto detect did not work. However, you can tweak it by looking at xorg.conf

Here is mine, in case it helps. BTW, I also have a problem, but it is related to the resolution of the external monitor, which is stuck to the same as the LCD pannel, which is too low.

you can find xorg.conf at etc/X11/

phil

---

### Post by phileas on 2006-10-04
xorg.conf as xorg.txt attached

---

