---
title: "battery monitor not working"
date: 2008-01-20
forum: Hardware &amp; Laptops
---

### Post by pikaia on 2008-01-20
I'm using Xfce on an Ubuntu server install on an Old IBM 600e.  I've  installed all the apps (I think I want) but I can't seem to get the battery monitor to work.  I have it in the xfce panel and installed apm and added it to the /etc/modules to start at boot and turned acpi=off but the monitor always reads "50%%."

Is there a way to configure the apm or the xfce-battery-plugin, to get this to work?

Thanks.

---

### Post by jdratlif on 2008-05-28
THREAD NECROMANCY!

Sorry, I know this is old...

The xfce battery plugin only works with ACPI, and will only work if the /proc/acpi/battery/BAT?/state file is present.

So an APM laptop cannot use the XFCE battery plugin.

---

