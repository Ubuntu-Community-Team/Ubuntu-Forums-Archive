---
title: "ACPI brightness support on laptop HP NX7400 running Kubuntu"
date: 2006-12-28
forum: Hardware &amp; Laptops
---

### Post by grybba on 2006-12-28
I am running Kubuntu 6.10 on a HP notebook NX7400. I have problem with setting the brightness control through the ACPI. 

I have a /proc/acpi/video/C080/C13F/brightness file containing
```
levels:  100 51 30 37 44 51 58 65 72 79 86 93 100
current: 0
```
Commands like ```
echo "51" > brightness
```  change the brightness of the screen and they show in the log of acpid. I cannot make my notebook's HAL recognize it, and the Power Manager cannot adjust it while switching to the battery mode. 

I had Ubuntu 6.10 installed on this notebook first, and the Gnome power management was able to dim the screen while running on batteries. I attach a result of the lshal command. If anyone could help with making the hald aware of the brightness adjustments I would be able to use my notebook for a bit longer while running on batteries. Thank you very much.

---

