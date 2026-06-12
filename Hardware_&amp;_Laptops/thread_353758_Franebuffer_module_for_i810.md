---
title: "Franebuffer module for i810"
date: 2007-02-05
forum: Hardware &amp; Laptops
---

### Post by CheeseEatingBulldog on 2007-02-05
I have a question which has been bugging me for some time now, and that is namely to get usplash to work as well as having a full screen console. 

I am trying to get a sony vaio pcg-r600mx to cooperate, which will only do a 640x480 console (x does run the desktop at full screen no problems). I have tried to add different 'vga=xx' to the grub list but all give "no usable theme for 640x480", or "unsupported modes selected". (It is pointless to set usplash.conf to a larger res, as the console is still 640x480).

Anyway, I did some reading up and found some refrences to some kind of fb module that would be able to do vesa-fb alongside the i810 used for the desktop. The thing is there was also reference to the fact that this module would be built in, in the 2.6 linux kernel. So, my question is do I download the fb module (which was last updated in 2002 or something) from sourceforge, or does anyone know how to force the vesa-fb module on bootup?

Thanks in advance.

---

### Post by CheeseEatingBulldog on 2007-02-05
I found [http://www.mjmwired.net/kernel/Documentation/fb/intel810.txt](http://www.mjmwired.net/kernel/Documentation/fb/intel810.txt) which shows some sort of howto, but if I have the i810 driver, do I also have the i810fb driver?

--edit--
I have found that the 2.6 kernel does have a i810fb.ko, but have no idea how to use it, or how to compile / patch it into my kernel. Can anyone help me please?

---

