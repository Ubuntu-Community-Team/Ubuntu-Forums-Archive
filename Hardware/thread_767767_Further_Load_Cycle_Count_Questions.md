---
title: "Further Load_Cycle_Count Questions"
date: 2008-04-25
forum: Hardware
---

### Post by JimmyK377 on 2008-04-25
Hey all, I'm testing the ugly fix before I upgrade to Hardy. I have tried both:

sudo hdparm -B 254 /dev/sda
sudo hdparm -B 255 /dev/sda

Both seem to have done the trick (miraculously the temperature of the hd seems to have actually gone down on average by 1 degree) and the load_cycle_count has stopped increasing.

The only difference being the response when I first enter them into the terminal.

With -254 I get:
setting Advanced Power Management level to 0xfe (254)

With -255 I get:
setting Advanced Power Management level to disabled

Which one should I use, 255 looks logical, but is there actually any difference, is there any benefit elsewhere with APM level at 0xfe (254) compared to disabled?


Also, there seems to be conflicting reports, will the ugly (why is it called that anyway?) fix work in Hardy?


EDIT:
and is -128 a suitable value for the ugly fix when on battery? It cycles about once every five seconds!


Thankyou,
JimmyK

---

### Post by JimmyK377 on 2008-04-26
Anyone?

---

