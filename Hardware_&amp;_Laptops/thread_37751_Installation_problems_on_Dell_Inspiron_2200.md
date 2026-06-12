---
title: "Installation problems on Dell Inspiron 2200"
date: 2005-05-28
forum: Hardware &amp; Laptops
---

### Post by wellparp on 2005-05-28
I have installed hoary on my new Dell Inspiron 2200. Everything works ok until x tries to start. The screen goes totally blank. I can hear the sound from the gnome login screen but no screen. Can someone please help me because if I cannot get ubuntu to work I will have to return the laptop.

---

### Post by wellparp on 2005-05-28
I now managed to start X by changing /etc/X11/xorg.conf under 

Section "Device"
# ...
# Changed the driver to vesa.
Driver "vesa"
#...
EndSection

So now ubuntu boots ok. Should I file this as a bug?

---

### Post by kenworth on 2005-05-28
Wellparp, you are a savior! O:) 

I have spent many days trying to figure out why Warty, Mandrake and even Hoary 'live' will run on my Dell Inspiron 2200, but Hoary X was failing after install.

Yes, there is a bug that should be reported. I was one more install away from dropping ubuntu from my 4 PCs and going back to Mandrake !

Thanks again.

---

### Post by wellparp on 2005-05-29
I am happy I could be of help! This is now filed as bug #11283 at bugzilla.ubuntu.com

---

### Post by MetalMusicAddict on 2005-06-09
Its funny I just bought the same laptop and this was my same solution. :) The vesa is a generic driver though. Is their a correct driver we could change it to? So we can get accelleration. In windows the chipset is ID'ed as i915. I changed "vesa" to "i915" and no go.

Also did you get the 1370 Internal Wireless card? I havnt got it workin yet.

---

