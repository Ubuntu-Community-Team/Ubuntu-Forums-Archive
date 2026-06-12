---
title: "Intel skylake and dual graphics support"
date: 2016-04-27
forum: Hardware
---

### Post by erkanea on 2016-04-27
Hello,
 I tried Xubuntu and other variants of Ubunt 16.04 and had same problem all the time. My notebook has Intel HM170 chipset, I7 6700HQ skylake CPU, Intel HD 530 and Nvidia 940MX dual GPU. Unfortunately there is no option in BIOS to disable the NVidia GPU and I actually don't need it. My problems were :

[LIST]
[*]Power buttons is always orange meaning computer is sleeping (not much important)
[*]With default drivers, Intel GPU is in use but resuming after suspend cause mouse pointer not to be shown
[*]If I install proprietary drivers, I can actually select to use Intel GPU but mouse pointer problem exists
[*]In drivers application I see an unknown device related to processor microcode. How can I fix it?
[*]In VMWare workstation, using NAT network adapter guest OS's can not connect to internet without manually setting the DNS server to google DNS or other external ones. They can ping the default gateway, so there must be something that prevents DNS server of VMWare to communicate with guests. 
[/LIST]

By the way, I tried kernel 4.5 and 4.6 lates rc and problems seems to be still there.

---

