---
title: "USB wifi adapter installation"
date: 2013-07-12
forum: Hardware
---

### Post by disabled_biscarri on 2013-07-12
Hi everybody,

I'm trying to install a USB wifi adapter in my Ubuntu workstation. The adapter is a Sitecom, model WLA-2102v1001.

The installation CD contains only windows and mac drivers and automatic installation procedures for this operating systems.

The wifi adapter's chipset is a Realtek RTL8192 and I have downloaded linux drivers from Realtek website.

I need help to manually install this linux drivers in my Ubuntu workstation, in order to get started using the USB wifi adapter:

[LIST]
[*]where to copy drivers in the workstation
[*]what configuration steps should I follow, system files to edit and so on...
[/LIST]

I will appreciate any help on this issue.

Lluís Biscarri

---

### Post by jp734 on 2013-07-14
If I remember it right, this is what I did. Execute each commands on terminal 

./configure
sudo make
sudo make install
sudo modprobe "module_name"

after executing the make command, pay attention to the module name it created for you and use that on modprobe. That should be it.

---

