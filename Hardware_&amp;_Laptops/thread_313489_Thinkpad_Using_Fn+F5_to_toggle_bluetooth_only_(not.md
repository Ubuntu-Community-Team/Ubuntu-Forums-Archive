---
title: "Thinkpad: Using Fn+F5 to toggle bluetooth only (not WIFI)"
date: 2006-12-06
forum: Hardware &amp; Laptops
---

### Post by apalacheno on 2006-12-06
Hey list,
I have an IBM/Lenovo ThinkPad Z61m. Everything works like a charm, except for a small annoyance:
Fn+F5 function key toggles all wireless, including WiFi, which is not what I want. It should only toggle bluetooth, leaving WiFi on.

Any advice?

Cheers,
apalacheno

---

### Post by djf_jeff on 2006-12-06
I don't think you can do this. I think this is a hardware switch, not controlled by software. So, when you press the button, it turn on/off both wifi and bluetooth.

---

### Post by matthewn on 2006-12-06
I don't think that's the case; I think the behavior is controlled by software. On my Thinkpad X31 with integrated bluetooth and wifi, under Windows pressing Fn+F5 brings up a dialog that lets me select which wireless tech to toggle on/off. But under Ubuntu, it's an all-or-nothing toggle. I imagine apalacheno is hoping for something similar to the behavior under Windows.

---

### Post by apalacheno on 2006-12-07
Yes exactly. As far as I can remember (the preinstalled Windows hasn't survived for very long on the Laptop) the behaviour in Windows was the same as matthewn mentioned.

---

### Post by djf_jeff on 2006-12-07
I cannot say this for sure but under Windows, there is simply an IBM driver that intercept the buttons call and launch the application you see. If you install a straight Windows without any drivers, the button will simply toggle like on Linux.

Under Linux, I just think that everything is done in hardware. I cannot be sure but on my laptop, I have compiled several kernel starting from scratch and I did not activate anything but the buttons keeps working.

---

