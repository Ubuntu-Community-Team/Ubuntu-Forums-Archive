---
title: "pciehp &amp; shpchp?!?"
date: 2004-12-29
forum: Hardware &amp; Laptops
---

### Post by paradox on 2004-12-29
pciehp
shpchp

Is used for? Detected pci card? So, if response is affermative, is indispanesable, for exemple, for detecting sound card?

TNX!

---

### Post by Rancoras on 2004-12-29
All I know is that they're part of the hotplug system.  pciehp - I guess would stand for PCI-Express Hot Plug?  No idea what the other one is.  Maybe a google is in order?

---

### Post by paradox on 2004-12-30
humm...i'm working about hotplug freeze at boot...i think this modules is possible cause...any person have experiance with hotplug crash?

TNX!

---

### Post by Rancoras on 2004-12-30
Well, why didn't you ask that in the first place?  hehe

[http://ubuntuguide.org/#modprobefatalerror](http://ubuntuguide.org/#modprobefatalerror)

That should fix it up  :D

---

### Post by paradox on 2004-12-30
[QUOTE=Rancoras]Well, why didn't you ask that in the first place?  hehe

[http://ubuntuguide.org/#modprobefatalerror](http://ubuntuguide.org/#modprobefatalerror)

That should fix it up  :D[/QUOTE]

yes I see this guide but my system don't show an error message for pciehp & shpchp. Anyway, just for once, my system freeze at boot (loading hotplug...). I have posted a message for this problem and after latest freeze i execute: 

$ grep hotplug /var/log/* (suggested command in other post...) 

but this is no relevant. So, i see all syslog file and I isolate the part of hotplug execution. Well, this part load in order:

1) Floppy informations
2) agpgart interface
3) ohci_hcd and all HUB USB interfaces (usb mass-storage etc...i have keyboard and mouse USB...)
4) pciehp & shpchp
5) ethernet card module
6) ACPI
7) gameport
8) ieee1394

Now, i don't think 1,2,3,5,7,8 (i'm dubious for ieee1394 port...) cause a hotplug crash (my module for ethernet card is 3c59x....in others systems this never don't cause any problem...). So, in my opinion, pciehp & shpchp and ACPI pheraps cause this problem. In other acpi, pciehp and shpchp handling IRQ and interrupt in general, and IRQ cause stranges problems often...

You have others considerations? (Sorry for my bad english!)

---

### Post by paradox on 2005-01-04
Any?  :confused:  :D

---

### Post by daver on 2005-01-16
[QUOTE=Rancoras]Well, why didn't you ask that in the first place?  hehe

[http://ubuntuguide.org/#modprobefatalerror](http://ubuntuguide.org/#modprobefatalerror)

That should fix it up  :D[/QUOTE]


That FAQ response gives very dangerous advice.

It is not a good idea to turn off warnings.  They are there for a reason and these modules should load.   This particular set of failures can lead to melted CPU's if the ACPI modules do not load.  If the shpchp module fails to load,  ACPI modules like THERMAL and FAN load, but they may not work.   That is the case on my laptop.

---

