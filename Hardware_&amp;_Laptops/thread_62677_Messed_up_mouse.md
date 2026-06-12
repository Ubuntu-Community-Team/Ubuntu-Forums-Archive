---
title: "Messed up mouse"
date: 2005-09-05
forum: Hardware &amp; Laptops
---

### Post by Mozzer on 2005-09-05
I foolishly rushed into a Howto about configuring a 5 button mouse. I wanted the thumb buttons to work like they do on Windows - back and forward. Alas, somewhere along the line, it all went wrong and now my scroll wheel goes Back when you try to scroll up and Forward when you try to scroll down!

Any help here is much appreciated.

Mozzer

---

### Post by s_p_a_r_k_y on 2005-09-05
mozzer, hope this teaches the value of keeping backup xorg.conf files lying around so you can compare and contrast from a known "working" file to a "screwed up" one. Try commenting out any option lines in your xorg.conf in the mouse section. This should return it to its original state. Then maybe post your mouse section for us to inspect

---

### Post by Mozzer on 2005-09-06
It's alright; after uninstalling imwheel I thought it would be fixed when I logged out and back in but it didn't so I panicked. However, after I switched back on this morning all is well. I think I've learnt my lesson :)

---

