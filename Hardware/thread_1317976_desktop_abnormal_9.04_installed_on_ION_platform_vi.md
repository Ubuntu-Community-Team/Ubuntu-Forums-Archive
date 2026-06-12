---
title: "desktop abnormal 9.04 installed on ION platform via hdmi to lcd tv"
date: 2009-11-07
forum: Hardware
---

### Post by tigerszheng on 2009-11-07
Hi,there:
 
I installed the nvidia 190.42 driver on ion 330 platform, it's running very well on my 40 inch full hd sony lcd tv and 42 inch full hd toshiba lcd tv.
 
but when I run it on my friend's samsung 40 inch hd(1280*720)  lcd and lg 47 inch full hd lcd tv, the problem comes out.
 
the problem is that the desktop is span out the screen, part of  the top pan is inside the screen and part of top pan  is outside the screen (like half inside the screen and half outside the screen), the bottom panel is the same.
 
when I use nvidia xsetting to adjust it, it informed that it's failed when saving to xconfig.bak, then I chmod 777 /etc/Xorg(i think maybe this is the problem), it indeed now the configure file can be saved, but the situation is the same after I reboot the gdm service.
 
Could someone tell me how to configure to suit every lcd tv(no mater pixel and sizes)?
 
All the best!

---

### Post by tigerszheng on 2009-11-07
googling, and found that's because overscan of tv.
 
but still doesn't understand how to adjust it?

---

