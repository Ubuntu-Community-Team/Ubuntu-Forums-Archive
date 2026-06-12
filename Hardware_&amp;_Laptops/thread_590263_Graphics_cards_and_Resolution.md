---
title: "Graphics cards and Resolution"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by SRX on 2007-10-24
Hi 

I recently installed Ubuntu 7.10 and right out of the box I was able to run at 1024x1280. I tried to put on the desktop effects but if required a graphics card, so I installed the Nvidia 6150 le drivers and then the resolution was only able to run at 1024x768 

does this mean my graphics card is not able to run at a higher resolution and I should get a better one like the [XFX GeForce 8600 GT XXX ]("http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=3048552&Sku=P450-8650")

 or
 
is it just because of Ubuntu 

thanks 

SR

---

### Post by SRX on 2007-10-24
Thanks

---

### Post by K.Mandla on 2007-10-24
Threads merged. :)

By the way, it could be an issue with the card, but more likely there's a setting somewhere that needs adjusted. Look in the display settings dialogue, or directly edit the screen sizes you want with this command in a terminal.

```
sudo nano -w /etc/X11/xorg.conf
```
I doubt it's a problem with the card; 6150s are relatively new. Good luck! :)

---

