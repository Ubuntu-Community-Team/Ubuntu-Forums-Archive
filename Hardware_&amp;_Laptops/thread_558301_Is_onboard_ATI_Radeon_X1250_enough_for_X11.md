---
title: "Is onboard ATI Radeon X1250 enough for X11?"
date: 2007-09-23
forum: Hardware &amp; Laptops
---

### Post by kinotix on 2007-09-23
I'm planning on a new desktop for Ubuntu, not for 3D gaming, and I'm considering:
Motherboard: Asus M2A-VM HDMI, with integrated graphics ATI Radeon X1250 (up to 1024Mb shared), and DVI-D output to connect to a 1680x1050 22'' TFT
CPU: AMD Athlon X2 +4200
RAM: 2GB DDR2 800MHz CL5 (or CL4)

The point is whether this X1250 graphics will be good enough to work snappily over the heavy X11/GTK 2/...

If I would take a dedicated and more powerful graphics, can I achieve a better experience with the GUI or is that totally worthless and only affects gaming and 3D rendering?

Thank you for any advice.

---

### Post by angryfirelord on 2007-09-23
Heck, that's more than you'll ever need to run gnome and gtk/qt apps. 2D acceleration is good on pretty much any card these days.

However, the open-source ati driver doesn't work with the X1000 series. You'll have to use the proprietary fglrx driver if you want 3D acceleration or resolutions beyond 1024x768.

---

### Post by Trollslayer on 2008-04-21
I have an Abit I-F90 which uses the X1250 and under 7.10 it is fine (use the restricted driver to get HD decode acceleration).

---

