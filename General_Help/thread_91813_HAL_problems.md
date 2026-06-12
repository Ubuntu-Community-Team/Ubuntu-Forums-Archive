---
title: "HAL problems"
date: 2005-11-18
forum: General Help
---

### Post by E1000 on 2005-11-18
When I start my computer normally, it will give me about 30 seconds from when i touch the keyboard to when it completely freezes, so i can barely log into Gnome even if im working fast

I restarted in recovery mode and ran "startx" as root and got the message 
"failed to initalize HAL" 
I think this is why its freezing when i log in normally

according to another post on this forum the way to see what is wrong is by typing
"/usr/sbin/hald --daemon=no --verbose=yes"
after entering that, i got this error.
```
23:57:42.895 [I] acpi.c:825: acpi_add: acpi_path=/proc/acpi/processor/CPU0 acpi_type=1, parent=0x00000000
23:57:42.908 [I] acpi.c:797: Add callouts completed udi=/org/freedesktop/Hal/devices/acpi_CPU0
23:57:42.909 [I] hald.c:89: Added device to GDL; udi=/org/freedesktop/Hal/devices/acpi_CPU0
23:57:42.909 [I] hald.c:640: Device probing completed
23:57:42.909 [I] hald_dbus.c:2787: entering
23:57:42.909 [E] hald_dbus.c:2794: dbus_bus_get(): Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
23:57:42.909 [I] util.c:1148: Killing helper with pid 7806
23:57:42.909 [I] util.c:1148: Killing helper with pid 7805

```

what is that "hald_dbus.c" thing, is this where the error is? how can I fix it?
the wierd thing is that this hapened only after i updated the acpi from an automatic update, would downgrading it help? how could I downgrade using apt?

---

### Post by E1000 on 2005-11-18
any ideas? im dying here,

what if I downgraded to the HAL from Ubuntu 5.04 (i never had any problems like this in the previous version)?

 ID really like to try that but i have no idea where to download individual DEB packages related to ubuntu, anybody got ideas?,,,

---

