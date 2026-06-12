---
title: "Wireless switch on Sony Vaio TR"
date: 2005-11-15
forum: Hardware &amp; Laptops
---

### Post by scubajeff on 2005-11-15
My Sony Vaio TR2 has a wireless switch which switch on/off the WiFi network interface. Breezy doesn't recognize it. So I study the ACPI output from the file "/var/log/acpid" and found out the switch indeed post an ACPI event (sony/hotkey SPIC 00000001 00000026) when I turn it on. So I create a new acpi event file under /etc/acpi/events directory to catch this event and then using wifi-radar to turn on my wireless connection automatically. Here is the acpi event file /etc/acpi/events/sony-wifi-on:

```

# /etc/acpi/events/sony-wifi-on

event=sony/hotkey SPIC 00000001 00000026
action=/usr/sbin/wifi-radar -d

```

Hope this would help.

---

