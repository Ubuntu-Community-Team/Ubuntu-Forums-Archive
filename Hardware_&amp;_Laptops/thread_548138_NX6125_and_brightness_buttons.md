---
title: "NX6125 and brightness buttons"
date: 2007-09-10
forum: Hardware &amp; Laptops
---

### Post by xMaximex on 2007-09-10
How can I make these buttons (fn+f9 fn+f10) to adjust screen brightness ?

I have a NX6125

---

### Post by kestas.j on 2007-09-11
In my case the brightness adjustment is seen only after x.server is restarted. Try to increase/dectrease a little bit and restart x server by pressing ctlr+alt+backspace. I thave happened to me after proprietary ATI driver was installed, and without it the monitor output was not working.

kestas.j

---

### Post by xMaximex on 2007-09-11
Yes it's working ! thanks

But is there a way to make these buttons works without restarting X ?

---

### Post by mar_rud on 2007-10-09
Most common "fix" is to switch to console (Ctr+Alt+F1), adjust brightness to Your needs (Fn+F9/F10) and go back to X (Ctrl+Alt+F7 ?):
[http://gentoo-wiki.com/HARDWARE_HP_Compaq_nx6125_with_Turion64](http://gentoo-wiki.com/HARDWARE_HP_Compaq_nx6125_with_Turion64)

---

