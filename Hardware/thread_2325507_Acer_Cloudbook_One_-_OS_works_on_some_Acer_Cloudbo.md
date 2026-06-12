---
title: "Acer Cloudbook One - OS works on some Acer Cloudbooks but refuses to boot on others"
date: 2016-05-23
forum: Hardware
---

### Post by cristianomaria-cumer on 2016-05-23
I have 6 Acer Cloudbook One, 4 of them are working perfectly with ubuntu 16.04 or 14.04 without any special kernel parameter with UEFI. 2 of them won't boot. In UFEI mode I simply get a black screen and in legacy I can see that there is a problem with IOAPIC + timer. If I use those kernel parameters:

noapic edd=off modprobe.blacklist=pinctrl_cherryview,sdhci_acpi

the system boots but it's not able to recognise the internal eMMC. If I try to load sdhci_acpi when the system is booted modporbe hangs. I have checked, same bios version, same mfg date, same motherboard revision. I can't understand what's wrong.

---

