---
title: "Fujitu-Siemens S7110 wrong resolution"
date: 2006-10-21
forum: Hardware &amp; Laptops
---

### Post by skitt on 2006-10-21
I have installed (k)ubuntu on my FJS S7110. Mostly successful. But I am unable to get my screen working good. The screen is detected automatically to 1400x1050 resolution, and so it says in the xorg.conf file to. But resolution turns out 1280x... nevertheless. 

Tried to run dpkg-reconfigure xersver-xorg, and screen is identified 1400x1050, but I get 1280 again. I refered to this page: [http://www.rfc1149.net/linux-s7110.html.en](http://www.rfc1149.net/linux-s7110.html.en) , which seemingly got it right, but there was less details on how he did it.

What do I do? Wrong resolution makes the screen really blurry :(

---

### Post by atte on 2006-11-14
I got it working. I think it the trick was '915resolution' (package):

"This modification is necessary to allow the display of certain
 graphics resolutions for an Xorg or XFree86 graphics server."

Peace,
atte

---

