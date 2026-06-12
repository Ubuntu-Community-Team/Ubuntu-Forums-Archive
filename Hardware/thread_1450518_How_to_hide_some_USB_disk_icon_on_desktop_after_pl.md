---
title: "How to hide some USB disk icon on desktop after plugged?"
date: 2010-04-09
forum: Hardware
---

### Post by voodoo_cat on 2010-04-09
In default setting, Ubuntu will show USB disk icon on desktop, and let file manager to open it automatically after the disk is plugged. I want some special USB disk will not do these things but others still do.

This USB disk will be shown with label "FX_RAM_DISK", and it is mounted to /media/FX_RAM_DISK folder. 

I can add some contents to the file named "/usr/share/hal/fdi/policy/10osvendor/20-storage-methods.fdi" to hide all USB disks.

[COLOR=Red]<match key="storage.removable" bool="true">
       <merge key="storage.automount_enabled_hint"  type="bool">false</merge>
</match>[/COLOR]

[COLOR=Black]I try to match disk label in this policy as below, but I fail.
[COLOR=Red]
[/COLOR][/COLOR][COLOR=Red]<match key="storage.removable" bool="true">
       <match key="storage.label" string="FX_RAM_DISK">
             <merge key="storage.automount_enabled_hint"  type="bool">false</merge>
       </match>
</match>[/COLOR]

[COLOR=Black]I also know the disk device name(sd*), PID/VID, vendor name and product name info. I wish to write a policy according to these information to hide special USB disk. 

Anybody can help me? Thanks.
[/COLOR][COLOR=Black]
[/COLOR]

---

