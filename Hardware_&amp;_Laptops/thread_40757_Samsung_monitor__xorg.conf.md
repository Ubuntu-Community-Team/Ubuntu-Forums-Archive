---
title: "Samsung monitor / xorg.conf"
date: 2005-06-10
forum: Hardware &amp; Laptops
---

### Post by bach on 2005-06-10
I have recently installed Ubuntu 5.04 on my desktop. My monitor is Samsung SyncMaster 955DF. Here is what I have in /etc/X11/xorg.cong

Section "Monitor"
Identifier "SyncMaster"
Option "DPMS"
EndSection

What should I add (refresh rates and, especially, modelines) in order to optimize it for my monitor? (I note the image "trembles" a little...)

Thanks in advance.

---

### Post by Njall on 2005-06-10
Are you asking how to do this or just what choices you have?  Here's what Samsung sez about the [SyncMaster 955DF](http://product.samsung.com/cgi-bin/nabc/product/b2c_product_detail.jsp?prod_id=AN19JSBTK) 

# CRT Size/Viewable: 19"/18"
# Horiz. Dot Pitch: 0.20mm
# CRT Type: DynaFlat
# Horizontal Scan: 30-85 kHz
# Max Resolution: 1600x1200 @ 68Hz
# Emissions: TCO '95
# Available Color(s): Ivory, Black , Ivory

The "rates" are there.  The modelines should, given what I see here, be what you are comfortable with.  I personally do not go above resolution 1280x1024 because I'm getting old and cranky, er, farsighted.   It should easily be able to support the maximum colors.  You can put in as many mode lines as you want.  You only use one at a time.

---

