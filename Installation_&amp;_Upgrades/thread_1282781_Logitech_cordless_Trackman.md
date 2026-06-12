---
title: "Logitech cordless Trackman"
date: 2009-10-04
forum: Installation &amp; Upgrades
---

### Post by Canuck.old on 2009-10-04
Hello
    My Trackman started to work on Jaunty 9.04 when I installed
this info as recommended.

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
<device>
<match key="info.product" string="Logitech USB Trackball">
<merge key="input.x11_options.Buttons" type="string">5</merge>
<merge key="input.x11_options.ButtonMapping" type="string">1 8 3 4 5 6 7 2 9</merge>
<merge key="input.x11_options.EmulateWheel" type="string">true</merge>
<merge key="input.x11_options.EmulateWheelButton" type="string">8</merge>
<merge key="input.x11_options.EmulateWheelTimeout" type="string">300</merge>
<merge key="input.x11_options.XAxisMapping" type="string">6 7</merge>
<merge key="input.x11_options.YAxisMapping" type="string">4 5</merge>
<merge key="input.x11_options.ZAxisMapping" type="string">4 5</merge>
<merge key="input.x11_options.Emulate3Buttons" type="string">true</merge>
</match>
</device>
</deviceinfo>

in the file mouse-wheel.fdi

The problem is that the "double click" "single click" stuff is confused
and inconsistent.

Can anybody help my wrist by making this thing work properly?

Thank you for your time.
dkr

---

