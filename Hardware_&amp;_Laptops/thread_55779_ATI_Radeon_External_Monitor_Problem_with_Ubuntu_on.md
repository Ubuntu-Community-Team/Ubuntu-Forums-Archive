---
title: "ATI Radeon External Monitor Problem with Ubuntu on a Dell Inspiron 9300"
date: 2005-08-10
forum: Hardware &amp; Laptops
---

### Post by phibuntu on 2005-08-10
I have a great Laptop with a great operating System (Ubuntu).

But my Screen resolution ist just a bit too great for an external monitor or Beamer.

When I connect my Laptop to a beamer, there are about 5 cm (2'') of the left side, which are not projected.

I tried to reduce the screen resolution from 1900x1200 to 1024x768.

But still (even with the low resolution of 1024x768 on the Laptop screen) the 5 cm are missing on the projector.

                

           Seen on the Laptop (x and o)

xxxxxxxxxxxxxxxxooooooooooooooooooooooooo
x_______________o_______________________________o
x_______________o_______________________________o
x_______________o_______________________________o
x_______________o_______________________________o
x_______________o_______________________________o
x_______________o_______________________________o
x_______________o__visible on the beamer (o)___o
x_______________o_______________________________o
x_______________o_______________________________o
x_______________o_______________________________o
x_______________o_______________________________o
x_______________o_______________________________o
x_______________o_______________________________o
xxxxxxxxxxxxxxxxooooooooooooooooooooooooo
         


PS: I am not sure, if this is the right discussion forum. Probably I have to look somewhere in the XF86-Places (but where are they?)


Any Ideas :?:

---

### Post by phibuntu on 2005-09-27
I have finally found an xorg.conf-File which solves the problem:

[http://rtr.ca/dell_i9300/xorg.conf]("http://rtr.ca/dell_i9300/xorg.conf")

Even having the laptop in full resolution "1920x1200 wuxga", it comes well scaled on a Toshiba TDP-T80 Beamer :)

---

### Post by vav on 2007-07-12
The 'radeon' driver, which I usually use (works great for suspend-resume) shows clipped edges so I tried using this xorg.conf, but it didnt work :( The 'ati' driver just didnt show anything on the projector

How do I debug? Any solution to this? I'd love to keep the radeon driver (I've currently changed the driver to radeon in the xorg.conf from the above post). Dont want to boot XP to run the projector :(

Thanks!

---

