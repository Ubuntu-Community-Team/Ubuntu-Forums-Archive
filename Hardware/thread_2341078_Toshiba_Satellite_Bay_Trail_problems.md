---
title: "Toshiba Satellite Bay Trail problems"
date: 2016-10-24
forum: Hardware
---

### Post by kyaustad on 2016-10-24
Hi,

Shortly after trading a tablet for a Toshiba Satellite Click 2 (Hybrid touchscreen laptop) I installed Linux. I soon found out that there is a bug in the kernel that results in Linux intermittently crashing on BayTrail integrated graphics devices. So to make sure it wasnt an installation problem I tried out different Ubuntu desktop environments distros and other Linux distros like Manjaro. Same problem. I installed Android x86 and the same problem occurs. It will be running fine and then it shuts off without any warning as if the battery were yanked from the device or the power plug was pulled. Dead. I then have to boot it back up. I installed Windows 10 and it doesnt crash so it is for sure that bug. I googled and found the **[B]"**intel_idle.max_cstate=1" [/B] kernel boot flag. As well as the boot flag [COLOR=#000000]"[/COLOR][COLOR=#000000]intel_pstate=disable".[/COLOR]

I applied these boot flags both from the GRUB menu at boot and then in the /etc/default/grub file. I still get random crashes. They are not isolated to any action or application either. Any way to fix this? 

Any help is appreciated thanks!

[COLOR=#000000]

[/COLOR]

---

