---
title: "few HW problems with dell 1720 + 8.04"
date: 2008-08-03
forum: Hardware
---

### Post by vichovi on 2008-08-03
Hello,

1/
i have Ubuntu 8.04 on Dell Vostro 1720, and if i do hibernate/suspend and later try to wake up my laptop, ethernet card does not work...  i tried to activate wake on LAN in BIOS,  i tried restart networking service ...  but this does not helps.
ethernet card is : 
	Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller 

i found in var/log/messages error :
ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
but this probably have nothing common with my eth. card.

2/ 
next thing is that my graphics card NVIDIA 8600M GS (drivers installed by ENVY utility) have normal temperature 62 ºC ( = 143.6 ºF), thats to much, isnt it ? I have just few compiz things enabled and few windows on desktop.

NVIDIA X server settings - powermizer :
Adaptive clocking : enabled, BUT performance mode : Maximum performance (WTF? - why max. performace when adaptive clocking is enabled ?) 

GeForce 8600M GS, 512MB, VBIOS : 60.86.64.00.26, nvidia driver version : 173.14.09

thank you for tips

---

