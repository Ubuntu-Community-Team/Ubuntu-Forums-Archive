---
title: "Problems with Text Mode"
date: 2006-12-14
forum: Hardware &amp; Laptops
---

### Post by samy-delux on 2006-12-14
Hey guys,

I have installed Ubuntu Edgy on my Laptop for some time now...
But i have one Problem that I did not have before:
When I try to switch to text mode during boot (does that even work? and how?) or when I try Alt+Ctrl+F1 i only get a Screen with Pink and Yellow etc. artifacts.

My Laptop is a Acer Travelmate 8103 and works pretty well, except that i have to add the following line to the Xorg.conf before X will run.
```
Option		"MonitorLayout"		"LVDS,AUTO"
```

Is that the source of my trouble?
BTW, it worked in Dapper and Breezy...

The graphics card is an Radeon X700 and i have no ati driver installed, so I use the standart one shipped with Edgy!

Thanks for your help,
Samy

---

