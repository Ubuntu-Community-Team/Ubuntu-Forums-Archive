---
title: "setpci not working"
date: 2007-08-31
forum: Hardware &amp; Laptops
---

### Post by ctignor on 2007-08-31
i am trying to change the PCI latency on my sound card.

using the setpci command:

setpci -v -s 00:1b.0 latency_timer=ff

gives me:

pcilib: cannot open /sys/bus/pci/devices/0000:00:1b.0/config

any guesses as to why it can't open and edit this file?

thanks,

C>T>

---

### Post by ramjet_1953 on 2007-08-31
I have not used that command myself, but it sounds like you may need super user rights to use it.

Try preceding the setpci command with sudo

ie

[COLOR="Red"]sudo setpci -v -s 00:1b.0 latency_timer=ff[/COLOR]

Regards,
Roger :cool:

---

