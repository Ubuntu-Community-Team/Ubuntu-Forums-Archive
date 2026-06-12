---
title: "Asus N61jv high temp problem"
date: 2011-02-06
forum: Hardware
---

### Post by neven on 2011-02-06
Hi,
i have problem with my laptop Asus N61jv, when i use it just to surf net and maybe download some torrent, cpu temp is ~68C and fan is always om max, in older 9.04 i did not have those problems as i remember, also i have dual boot win7 and its quiet, working normal in win, when i do that $top command processor is busy below 10%, i just don't see logical explanation  why is overheating. I use ubuntu 10.10 btw.

Edit:
Not sure maybe this can help
acpi -V
Battery 0: Unknown, 98%
Battery 0: design capacity 4300 mAh, last full capacity 4066 mAh = 94%
Adapter 0: on-line
Thermal 0: ok, 72.0 degrees C
Thermal 0: trip point 0 switches to mode critical at temperature 93.0 degrees C
Thermal 0: trip point 1 switches to mode passive at temperature 87.0 degrees C
Cooling 0: LCD 0 of 15
Cooling 1: LCD 0 of 15
Cooling 2: Processor 0 of 10
Cooling 3: Processor 0 of 10
Cooling 4: Processor 0 of 10
Cooling 5: Processor 0 of 10

Edit2:
sudo sensors-detect
at the end its saying
"Sorry, no sensors were detected.
This is relatively common on laptops, where thermal management is
handled by ACPI rather than the OS."

---

