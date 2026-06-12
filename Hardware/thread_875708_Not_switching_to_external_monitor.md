---
title: "Not switching to external monitor"
date: 2008-07-31
forum: Hardware
---

### Post by kroiz on 2008-07-31
Howdy,
I got a new HP Pavilion laptop with 
Intel Mobile GM965/GL960 Integrated Graphics Controller.
It is a dual boot.
I connected it to an external monitor (LCD TV) and clicked Fn+F4 and nothing seems to happen.
The same thing on the windows that is on that laptop works.

Should I install something? Or make changes to xorg.conf?

---

### Post by Nepherte on 2008-07-31
A lot of those fn-keys just don't work in Ubuntu. Go to system > preferences > screen resolution. There should be an option to detect monitors.

That or either you type:
```
displayconfig-gtk
```
This might give you some options as well.

---

### Post by kroiz on 2008-07-31
I could not do it using the guis you suggested.
but in the "Screen and Graphics Preferences" in the tab "Graphics Cards" I see that the driver for my graphic card is vesa. I tried to pick intel 965 but when I test it with the "Test" button, I get Failure message.

---

### Post by Nepherte on 2008-07-31
I have the same graphic card and it uses vesa as well. I'd stick with those. The two suggestions I gave you worked for me. You could try using xrand, but I never used it so don't know how it actually works.

---

