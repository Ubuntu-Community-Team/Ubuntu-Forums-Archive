---
title: "WiFi fails after long suspend + notebook freezes on restart at the shutdown screen"
date: 2008-05-31
forum: Hardware
---

### Post by hotweiss on 2008-05-31
If I suspend my computer for a short time and resume my wifi will begin working without troubles. If I suspend for 12 hours or more my wifi will not work when I resume. It goes into offline mode and then when I put it back into online mode it still does not resume. I didn't have this problem with Ubuntu Hardy, but I do have it with Kubuntu Hardy. I tried the following solution, but I had no luck:

> sudo kate /etc/default/acpi-support

and then added this:

> STOP_SERVICES="networking"

...which didn't work. In addition, when my wifi stops working after a long suspend, my computer then freezes when I try to restart at the Kubuntu shutdown screen with the bar fully completed. I then have to do a hard shutdown.

Any ideas?

---

### Post by hotweiss on 2008-05-31
bump

---

