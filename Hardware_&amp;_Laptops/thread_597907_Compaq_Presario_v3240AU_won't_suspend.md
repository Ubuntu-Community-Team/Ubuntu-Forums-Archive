---
title: "Compaq Presario v3240AU won't suspend"
date: 2007-10-30
forum: Hardware &amp; Laptops
---

### Post by mangoHead84 on 2007-10-30
The laptop goes into suspend mode without a problem, but when I try to resume, the computer wakes up but the screen remains blank and the laptop is unresponsive to key commands (Ctrl+Alt+Backspace, Ctrl+Alt+F etc...) and the only option is to hold the power button down to hard reboot. This is after a clean install of Gutsy AMD64 version.

I have tied editing the '/etc/default/acpi-support' file setting the POST_VIDEO=false with no effect. 

I have also tried suspend with CompizFusion turned off with no difference in the behaviour. Hibernate works without problem. Does anyone know of any other methods of getting suspend to work?

Laptop specifications:
Make & model: Compaq Presario v3240AU 
CPU: AMD Turion TL-52 dual core chip
Memory: 512Mb 
Graphics Card: nVidia GeForce 6150 Go with the C51 chipset using the 'glx-new' driver
Motherboard: uses nVidia MCP51 chipset
Wireless Card: Broadcom Corporation BCM4312 using the 'bcm43xx' driver
HDD: 80 GB SATA drive

Everything else with Gutsy works out of the box with this laptop, this is the only really annoying problem.

---

### Post by inacoma on 2007-11-07
I have same issue on compaq 8510w...any solutions?

thanks!

ktp

---

