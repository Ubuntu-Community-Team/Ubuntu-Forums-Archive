---
title: "turn off suspend"
date: 2005-07-15
forum: Hardware &amp; Laptops
---

### Post by damnhappy on 2005-07-15
Hi all, 
I am trying to turn off the suspend function altogether for my hp pavilion zv5000. I opened this:  /etc/acpi/lid.sh  but couldn't figure out what to change. I am pretty new to linux, but am getting comfortable fast. 
Thanks!

---

### Post by elsewhere on 2005-07-15
I would just go into /etc/acpi/events/lidbtn and comment out the *action=/etc/acpi/lid.sh* line, this should prevent the script from running when your lid is closed.

I think you'll have to restart the acpi daeamon in order to reload the rules, using *sudo /etc/init.d/acpid restart* should do it.

Hope this helps...

Cheers,
KV

---

### Post by damnhappy on 2005-07-15
Worked like a charm! Thanks!

---

