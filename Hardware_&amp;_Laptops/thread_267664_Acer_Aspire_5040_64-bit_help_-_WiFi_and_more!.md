---
title: "Acer Aspire 5040 64-bit help - WiFi and more!"
date: 2006-09-28
forum: Hardware &amp; Laptops
---

### Post by riverty on 2006-09-28
First, thanks for replying and offering your help. It is very much appreciated!

OK - so I have Kubuntu 6.06 64-bit installed now. To clarify, I have to have the 'acpi=off' option passed to the kernel or the kernel will simply not boot. I get a kernel panic on boot without this passed. I ALSO have the 'noapic' option passed as I have found that without this option, NONE of my network controllers will work including wired network.

I have been following the instructions found here:
[https://help.ubuntu.com/community/WifiDocs/Acer5021WLMi_Amd64](https://help.ubuntu.com/community/WifiDocs/Acer5021WLMi_Amd64)
to try and get the wireless controller to work. The instructions work all the way to 'modprobe acer_acpi' and this fails with 'FATAL: Error inserting acer_acpi (/lib/modules/2.6.15-27-amd64-generic/extra/acer_acpi.ko): No such device'. I'm thinking that the reason for this is because I have to pass the 'acpi=off' option to the kernel but I'm not sure.

I might add that I do not have any power options as well. Again due to the fact that I have to pass the 'acpi=off' option. This option is really screwing me up!

Other things that I have done include adding 'blacklist bcm43xx' to /etc/modprobe.d/blacklist and making sure that 'alias wlan0 ndiswrapper' is in /etc/modprobe.d/ndiswrapper. I have also tried 'alias eth1 ndiswrapper'. Now on boot, I get in dmesg:

[   28.903486] ndiswrapper version 1.8 loaded (preempt=yes,smp=yes)
[   29.206527] ndiswrapper (load_pe_images:571): fixing KI_USER_SHARED_DATA address in the driver
[   29.207954] ndiswrapper: driver bcmwl5 (Broadcom,02/11/2005, 3.100.64.0) loaded
[   29.216534] ndiswrapper: using irq 10
[   30.222689] wlan0: vendor: ''
[   30.222693] wlan0: ndiswrapper ethernet device 00:16:ce:21:f0:b9 using driver bcmwl5, 14E4:4318.5.conf
[   30.222711] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK

Sounds good right? However, running ifconfig reports my wireless controller as eth1 - not good. It's also eth1 in Network Settings. It's enabled but does not work.

So this is where I'm at currently. What should I do or try next to get wireless working?

Thanks again!

---

