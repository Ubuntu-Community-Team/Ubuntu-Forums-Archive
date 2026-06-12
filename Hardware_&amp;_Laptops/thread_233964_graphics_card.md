---
title: "graphics card"
date: 2006-08-10
forum: Hardware &amp; Laptops
---

### Post by simukas on 2006-08-10
can i change my craphics card without messing anything up?(when i did that on my old ark linux i had to install everything all over again :-x :-x :-x :-x )

---

### Post by Dr. Nick on 2006-08-10
it will not really screw your system up, you may just be stuck with the command line until you reconfigure xorg to use your new card.

either edit /etc/X11/xotg.cong by hand, or run

sudo dpkg-reconfigure xserver-xorg

---

### Post by simukas on 2006-08-11
tnx..

---

