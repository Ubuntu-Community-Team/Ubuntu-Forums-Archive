---
title: "Battery undetected, cpu throttling problem"
date: 2005-06-16
forum: Hardware &amp; Laptops
---

### Post by D4_B34M on 2005-06-16
When I bought this Acer Aspire 1414 (1410 series) I knew wouldn't be easy to get Linux to it but here I am...

Wifi, screen resolution, temperature, etc. are now working after more than 10h of tweaking...

But newer thought; a problem with battery...

I have nothing on: /proc/acpi/battery and I cant see my battery status what is really a bad problem...

Also I think my CPU is not throttling as it should, my laptop is 50% hotter in linux than windows and theres less battery life in linux too...

What can I do about these? I really need to see battery status, can I for example use the drivers of windows on it with some emulator, or something like "ndiswrapper" but for all drivers.


Oh and HAL reports in OEM-specific:

bios.chemistry Lithium Ion
bios.design_capacity 4400mWh
bios.design_voltage 14800mV
bios.location Right Side
bios.manufacturer Sanyo
bios.maximum_error 6%
bios.name Sanyo


and other details...

---

### Post by D4_B34M on 2005-06-16
[http://lists.suse.com/archive/suse-laptop/2005-Jun/0043.html](http://lists.suse.com/archive/suse-laptop/2005-Jun/0043.html)

I just found that, the same problem... But different laptop and os.

Can anyone please help me to do this patch on ubuntu?

---

### Post by D4_B34M on 2005-06-16
Heh, i just patched my kernel (MY SELF!) :)

But still want to know why i have less battery life in Linux?

---

