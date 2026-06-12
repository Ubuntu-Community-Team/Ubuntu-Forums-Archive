---
title: "Unable to see battery status in &quot;Battery Charge Monitor&quot; applet"
date: 2006-12-14
forum: Hardware &amp; Laptops
---

### Post by mskadu on 2006-12-14
I added the battery charge monitor applet to my panel. However, it shows N/A next to the battery sign. According to its help, i did a:

cat /proc/acpi/battery/BAT1/info

it shows:

present:   no

I even tried setting no_hal pref to true as shown in the applets help. But doesnt help.

Any ideas? :-k

tia

---

### Post by Randori on 2006-12-14
It could be your BIOS.
Check your BIOS Manufacturer to see if its APCI Compatable.
Most Systems nowadays are but to be sure just check.

---

### Post by mskadu on 2006-12-15
Randori,

Thanks for your answer. Thats the curious thing you know. My screen dims and brightens when i take off my power cable and re-attach it. I believe this would not be possible if ACPI would not be working. Am i right?:-k

- Mayuresh

> **Randori said:**
> It could be your BIOS.
Check your BIOS Manufacturer to see if its APCI Compatable.
Most Systems nowadays are but to be sure just check.

---

