---
title: "Wacom Intuos Serial not working"
date: 2005-05-04
forum: Hardware &amp; Laptops
---

### Post by endrylthalan on 2005-05-04
I just tried to configure xorg.conf as wacdump worked perfectly but I still can't move the cursor.
When I'm modprobing wacom if i make an lsmod I get 2 wacom answers :
wacom which is used by noone
usbcore in which wacom is also listed
The problem is I have a serial tablet and I don't know how to fix that. Can anyone help me ? Thanks

---

### Post by plebeien on 2005-06-03
same problem for me.

---

### Post by endrylthalan on 2005-06-06
At last it worked I just had to re-install the wacom-utils package via synaptic and it ended up moving taking pressure etc...  :)

---

### Post by xsforis on 2007-01-18
I have an Intuos CD that is serial as well, I have gone over the xorg.conf file and used wacdump (which showed that the tablet is working fine) but still no joy. I really want to get this working, I hate to think that I might have to go back to windows. Is there any hope?

Cheers,
xsforis

---

