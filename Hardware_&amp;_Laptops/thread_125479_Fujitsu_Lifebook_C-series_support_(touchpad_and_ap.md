---
title: "Fujitsu Lifebook C-series support (touchpad and application panel)"
date: 2006-02-04
forum: Hardware &amp; Laptops
---

### Post by reedlaw on 2006-02-04
I have installed Breezy on a colleague's Fujitsu laptop and he is complaining about lack of support for his touchpad and application panel.  I tried configuring the touchpad using the synaptics driver and it works except for the middle scrolling buttons.  When I run xev I get button 1 for both the left mouse button and the down scroll wheel.  The up on the scroll wheel responds as button 2 and the right mouse button as button 3.  So obviously zaxis-mapping "6 7" is not going to work.
As for the application panel, I found a driver called apanel on sourceforge but it requires kernel sources and compiling.  Has anyone gotten both of these to work without the trouble of compiling the apanel driver?  Does this touchpad require a different driver?  I have heard some Fujitsu's use the Alps touchpad rather than synaptics.

---

### Post by stangbang on 2006-02-04
most fujitsu's have alps touchpads, but the synaptics driver in ubuntu will work with both. As for getting the middle scroll button to work This is somthing I have been trying to do myself, but have not been able to find anything to solve it. If you do find a solution on the scroll button please let me know what had to be done.

---

