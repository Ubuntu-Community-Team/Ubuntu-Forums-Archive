---
title: "How to enable large screen and wide screen support"
date: 2006-09-24
forum: Hardware &amp; Laptops
---

### Post by bluefuse on 2006-09-24
I have nopticed that alot of the new "acer aspires" and "apple" computer companies have a wide screen. This tid bit helped one indivual with a new acer laptop, hopefully it will help many others.


sudo gedit /etc/X11/xorg.conf

    * Add the following line to the appropriate "Monitor" section 

Modeline	"1920x1200" 154 1920 1968 2000 2080 1200 1203 1209 1235

    * For example the HP2335 should now look like: 

Section "Monitor"
	Identifier	"hp L2335"
	Option		"DPMS"
	Modeline	"1920x1200" 154 1920 1968 2000 2080 1200 1203 1209 1235
EndSection

---

