---
title: "No contact with mouse after starting up"
date: 2007-03-13
forum: Hardware &amp; Laptops
---

### Post by JanneHe on 2007-03-13
Each time I've started my computer the mouse is not detected unless I remove and reinsert the PS/2 contact.

This problem started after uppgrading from Breezy to Dapper and from gde to kde.

I've tried adding:  

modprobe -r psmouse
modprobe psmouse proto=imps

to the /etc/rc.local but that didn't make any difference.

Does anyone have an idea?

/J

---

