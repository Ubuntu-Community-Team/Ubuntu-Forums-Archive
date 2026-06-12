---
title: "intel ipw2200 wifi LED"
date: 2007-05-30
forum: Hardware &amp; Laptops
---

### Post by hardyn on 2007-05-30
how? has anybody been able to make this work...

its appears that there are provisions for it in the driver, but was unable to make it work... anybody else?

thanks.

---

### Post by Chal on 2007-05-30
to make the led wor just open/create this file:

~$ sudo gedit /etc/modprobe.d/ipw2200 

add this line:

options ipw2200 led=1 

and then restart and it should work fine

---

### Post by hardyn on 2007-05-30
cheers...

that was not a part of what i was trying.

thanks.

---

