---
title: "Touchscreen driver exists only for XFree"
date: 2005-04-29
forum: Hardware &amp; Laptops
---

### Post by neokod on 2005-04-29
Hi,

I want to put a driver for the touchscreen of a Fjitsu laptop Lifebook B Series :
[http://stz-softwaretechnik.com/~ke/lifebook/lifebook-2.6.html](http://stz-softwaretechnik.com/~ke/lifebook/lifebook-2.6.html)

But this driver exists only for XFree.

I'm under Hoary, is it possible to return to XFree without problem for future dist-upgrade ?

Thanks

---

### Post by Psquared on 2005-04-29
[QUOTE=neokod]Hi,

I want to put a driver for the touchscreen of a Fjitsu laptop Lifebook B Series :
[http://stz-softwaretechnik.com/~ke/lifebook/lifebook-2.6.html](http://stz-softwaretechnik.com/~ke/lifebook/lifebook-2.6.html)

But this driver exists only for XFree.

I'm under Hoary, is it possible to return to XFree without problem for future dist-upgrade ?

Thanks[/QUOTE]

You mean xorg 6.8+ does not support the touchscreen for a Tablet PC, but xfree does? Hmmm - that surprises me. I don't think you can go back without messing up and losing some other functionality.

Did it work on Warty? (Warty uses Xfree.)

---

### Post by Kimm on 2005-04-29
acctually... XFree86 does work in Hoary, games wount worj though since it brings your fps down quite alot

---

### Post by neokod on 2005-04-29
[QUOTE=Psquared]You mean xorg 6.8+ does not support the touchscreen for a Tablet PC, but xfree does?[/QUOTE]
Yes,
On the page of the driver I read :
"There are rumors (and patches) for edev-support for X -- but I wasn't able to get them to work thus I wrote this driver. Maybe it is integrated with a more general evdev support for X one day. "

[QUOTE=Psquared]
 Hmmm - that surprises me. I don't think you can go back without messing up and losing some other functionality.
[/QUOTE]
Yes but It's not very important, I need this touchscreen 

[QUOTE=Psquared]
Did it work on Warty? (Warty uses Xfree.)[/QUOTE]
I supposes but I can't try because the laptop doesn't have CDROM, we have use a hacks to install Ubuntu Hoary (with grub for dos)
But if Warty used XFree, I supposed the driver could be works on warty.


If i do a apt-get install xfree-common, I think this will make problem for next dist-upgrade ?

---

### Post by neokod on 2005-04-29
I'll try it.
And tell you if this works under X.org

---

