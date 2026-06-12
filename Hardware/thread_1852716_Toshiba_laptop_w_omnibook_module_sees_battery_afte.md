---
title: "Toshiba laptop w/ omnibook module sees battery after plug/unplug ac adapter, why?"
date: 2011-09-30
forum: Hardware
---

### Post by khamil8686 on 2011-09-30
i have Kubuntu 11.04 64-bit and the battery wasn't present according to /proc/acpi/battery. so i researched and found i needed a toshiba acpi module in my kernel. found that i needed the omnibook module instead of the toshiba acpi module because it gave me fatal errors when modprobing it. so now the battery is detected but it takes me plugging and un plugging my ac adapter cord. any way to get it to automatically update itself instead of requiring the ac adapter? thank you in advance! :)

--
it there a command i can run in a script to tell the kernel to probe the hardware again? ive tried to write to the /proc/acpi/BAT1/state file to see if it would do anything but no, read write error :) back to pokin around... pokepokepoke

---

