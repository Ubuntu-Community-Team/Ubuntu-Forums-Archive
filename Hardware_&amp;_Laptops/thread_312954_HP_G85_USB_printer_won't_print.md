---
title: "HP G85 USB printer won't print"
date: 2006-12-05
forum: Hardware &amp; Laptops
---

### Post by harambe on 2006-12-05
I have an HP OfficeJet G85 printer which works fine under Windows XP connected via USB.

I have followed the HPLIP install process, and the setup process within Ubuntu but can't get it to work.

Ubunto printer Setup recognizes the printer as a G85, and issues a TEST print without error, but nothing prints - the jobs remain queued.

Anyone got any ideas ?

---

### Post by harambe on 2006-12-05
Not sure if this adds anything useful to the problem definition, but having deleted the printer definition in CUPS and added a new one ( it auto detected the printer correctly ) I get the following in CUPS while it tries to print a test page :-

"open print channel failed; will retry in 30 seconds..."

and just carries on trying.

---

### Post by flyking on 2006-12-19
I'm having the exact same problem.

Hope someone can help.

---

### Post by newaustralian on 2007-01-24
Having similar problems using G85 all in one via USB  with live disk version of 6.10.

Configuration ok, print goes to the queue and I can see it there but printer does nothing.
Job disappears from print list.

I have tried several combinations of acpi on/off etc but no help.

Same thing happens with knoppix live cd.

All help appreciated

---

### Post by 11hjpphty76lkjj on 2007-01-24
Have you tried power cycling the printer and then connecting it to the system?

Can you run tail -f /var/log/messages

try and print and post the log?

---

