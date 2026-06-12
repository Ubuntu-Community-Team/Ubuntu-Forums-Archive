---
title: "Using nVidia GPU with server motherboard that has integrated VGA output"
date: 2021-01-21
forum: Hardware
---

### Post by PDiddlyDoodlyDo on 2021-01-21
Hi, I have a home server running on a ASRock Rack ROMED8-2T motherboard (64GB RAM, EPYC7262 AMD CPU), and I thought I might do some casual gaming on it as well... so I've bought a KFA2 GeForce GTX 1050Ti OC; installed the latest nvidia drivers; checked that the 1050Ti shows up on the output from 'lspci'; and I've tried installing a lightweight desktop (KDE) on top of the ubuntu server that's running on it:
- sudo apt install kde-desktop
- startx

When I connect a monitor to the integrated VGA I can see the desktop running. When I connect that same monitor to the display port (1050Ti display port <-> Monitor display port), I can't see anything.

Please help. What have I not done to enable the display port output?

---

### Post by mastablasta on 2021-01-21
disable the integrated VGA.

maybe you could use prime to switch the GPU but it is difficult to say.

---

### Post by CelticWarrior on 2021-01-21
> **mastablasta said:**
> disable the integrated VGA.

This ^^^. Prime or similar is only for laptops with switchable graphics, not the case here.
It must be explicitly selected in UEFI. [https://download.asrock.com/Manual/ROMED8-2T.pdf](https://download.asrock.com/Manual/ROMED8-2T.pdf) (p. 46)

---

### Post by PDiddlyDoodlyDo on 2021-01-23
> **mastablasta said:**
> disable the integrated VGA.

... Thanks @mastablasta that did the trick. For anyone else with this issue, in BIOS 1.30 the setting you need is under 'Advanced' > 'Chipset configuration' > 'Onbrd/Ext VGA Select'

 Set the value to 'External', and be careful to choose the correct PCIe slot for your discrete GPU - remember that the PCIe slots are numbered 1 to 7 from RIGHT to LEFT as you look at the IO shield from the rear of the computer/motherboard (i.e. if you have this in a tower, then slot 1 is the lowest one...). If you mess up this setting, then when you reboot, you'll have no video signal, and you'll have to reset your BIOS and start again.

Hope that helps.

---

