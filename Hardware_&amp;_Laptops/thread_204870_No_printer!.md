---
title: "No printer!"
date: 2006-06-27
forum: Hardware &amp; Laptops
---

### Post by TMC on 2006-06-27
Just upgraded from Breezy to Dapper and I've lost my printer from the system - it's an HP Deskjet 840c.  When I try to re-install it, the printer is detected OK but, on the second screen, the Manufacturer, Model and Driver boxes are blank with no options in any of them.  Checking on Synaptic shows that I have both hpijs and foomatic-db-hpijs installed.

What am I doing wrong?  ](*,) 

Many thanks in advance,

David Shaw

---

### Post by TMC on 2006-06-27
I've just tried installing through the CUPS frontend ([http://localhost:631/](http://localhost:631/)) and at least it gives me a selection of drivers to choose from - but I can't get it to authenticate.  It rejects both my username/password and root/password options

](*,) ](*,) 

David Shaw

---

### Post by TMC on 2006-06-27
Fixed it!  Turns out gnome-cups-manager hadn't been upgraded during the Ubuntu upgrade.  I noticed that Synaptic was telling me that it hadn't been upgraded when I installed something else.  Forced the upgrade and everything now works just fine  :D 

David Shaw

---

