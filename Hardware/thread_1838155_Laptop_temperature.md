---
title: "Laptop temperature"
date: 2011-09-03
forum: Hardware
---

### Post by Gekoncze on 2011-09-03
Hi, 
after trying many distros I finally found stable distro which is also user-friendly (ubuntu), but I came across a problem with temperatures. They seem to be too high:
harddisc: /dev/sda: WDC WD3200BEVT-22ZCT0: 57°C
other:
acpitz-virtual-0
Adapter: Virtual device
temp1:       +57.0°C  (crit = +95.0°C)
temp2:       +52.0°C  (crit = +95.0°C)
k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +61.0°C  (high = +70.0°C) 
Only the acpitz-virtual-0 looks ok. The k10temp-pci-00c3 gets sometimes to 69. (70 is marked as high)
Those temperatures are when I am just browsing web. When I play some games, the hddtemp reaches 60. I would like to know which one is temp of my gfx card (if it is listed here), because the names says nothing to me.
Laptop info: Packardbell easynote TJ 71, AMD Athlon X2 M300, gfx card is ATI (not sure which type because I dont know how to find HW comp. names in Ubuntu)
note: on Linux Mint I got lower temperatures with some kernel overheating fix, but I dont know if it works with ubuntu.

---

### Post by .... on 2011-09-03
The Mint fix is probably using 'pcie_aspm=force' on the boot line. You would add that to the GRUB_CMDLINE_LINUX string in /etc/default/grub and then run:
```
sudo update-grub2
```
> ATI (not sure which type)```
lspci
```> I would like to know which one is temp of my gfx cardProbably none of them.

---

### Post by Gekoncze on 2011-09-03
Thx, and another question, will this fix work when I have grub of some other distro?

---

