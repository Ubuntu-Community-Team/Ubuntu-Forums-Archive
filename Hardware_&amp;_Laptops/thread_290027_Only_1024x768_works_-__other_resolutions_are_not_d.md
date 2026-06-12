---
title: "Only 1024x768 works -  other resolutions are not displayed properly"
date: 2006-10-31
forum: Hardware &amp; Laptops
---

### Post by Emerpus on 2006-10-31
I just made a fresh installation of Edgy. When I try to change the screen resolution to 1400x1050 (which is my laptops native resolution) it looks a bit like someone put LSD in my cup of Ubuntu. The same goes for all other (higher) resolutions than 1024x768 (the graphics get currupted). Does anybody know how to fix this? 
On a side note my 4 year old laptop has an ATI Radeon Mobility M6 graphics chip if this has anything to say.

---

### Post by stream303 on 2006-10-31
I wonder if you are using the default driver..  Have you tried:

```
 sudo dpkg-reconfigure -fgnome -phigh xserver-xorg
```

and selected ATI followed by the resolution you want?  Gotta' feeling this might do it...

---

### Post by Emerpus on 2006-11-01
I followed your instructions and after a reboot it worked. Thanks for helping out a noob. :D

---

