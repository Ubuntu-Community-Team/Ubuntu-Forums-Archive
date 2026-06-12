---
title: "Fixing suspend in Acer Aspire One 751h"
date: 2009-10-02
forum: Hardware
---

### Post by pacoros on 2009-10-02
If somebody installed psb graphics driver into a AO751h should have noticed that suspend to RAM did not work anymore.

Wander Boessenkool posted a patch to hal mailing list with a fix. I hope to see it packaged soon. Until then, you can fix it by editing /usr/share/hal/fdi/information/10freedesktop/20-video-quirk-pm-acer.fdi and adding the following at the end (before the last </match>): 

```

<match key="system.hardware.product" string="AO751h">
   <merge key="power_management.quirk.dpms_on" type="bool">true</merge>
   <merge key="power_management.quirk.vbemode_restore" type="bool">true</merge>
   <merge key="power_management.quirk.vbestate_restore" type="bool">true</merge>
</match>

```

You can test if it works by clicking suspend at the top right menu.

Regards!

---

### Post by StMaus on 2009-10-09
At LAST! a solution that really worked! THANK-YOU! THANK-YOU!

I sure hope Koala has this built in.\\:D/

---

