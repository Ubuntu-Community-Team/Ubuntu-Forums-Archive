---
title: "kacpid and acpid"
date: 2008-09-20
forum: Hardware
---

### Post by zeek0us on 2008-09-20
Forgive me if I'm missing something obvious, but my googling has been fruitless to this point.

I'm trying to get my function keys to work on a VAIO VGN-FE790.  AFAIK, there's no working solution available, so I'm trying to cobble something together.  I've used acpid_listen to find that Fn+F5 gives the event of 
sony/hotkey SNC 00000001 00000010, which I want to bind to a command using smartdimmer to decrease screen brightness.

My understanding is that the events are handled through acpid, which listens for events like Fn+F5 being pressed, and then does whatever is listed in /etc/acpid/events.  So even though I've verified that I have the correct acpid event and that it's associated with a working script to decrease screen brightness, the whole process doesn't work as planned (i.e. Fn+F5 still does nothing).

In trying to figure out what's going on, I've noticed the processes "kacpid" and "kacpi_notify", which, judging by their names, are doing the same things I'm expecting from acpid and acpi_notify.  Are these kacpid processes running instead of or alongside acpid?  Can I replace kacpid with acpid?  I can't find anything using "locate kacpid" or "man kacpid" so I'm kind of at a loss as to what's going on here.

---

