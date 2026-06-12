---
title: "Alienware Alpha HDMI IN"
date: 2015-08-23
forum: Hardware
---

### Post by Kuro_Kitsune on 2015-08-23
Hello everyone I just got my hands on a alienware alpha just a few weeks ago running ubuntu 14.05 and its been running like a dream it is awesome. the only thing i cannot get to work is the HDMI IN port on the unit it has both a HDMI out and HDMI IN i have all the nvidia drivers installed. so for example i have the hdmi out leading the my monitor and the hdmi in is plugged into my Wii U It may be functional and I may just be too dumb to know what program to even start with to access it. 

lspci doesn't seem to show any extra devices so i assume it isn't even turned on/functional

video card is as follows 
01:00.0 VGA compatible controller: NVIDIA Corporation GM107M [GeForce GTX 860M] (rev a2)
Although from what i understand in this unit it is a custom GTX 860M but the normal nvidia drivers have been working great so far

thank you for any and all help. it have been years since I have made a post on the forums that i couldn't find an answer to by just looking around. even had to make a new user So i hope my posting doesn't offend anyone in any way. thank you again. ):P

also full lspci is as follows
```

kain@kain-ASM100:~$ lspci
00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5)
00:1c.5 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #6 (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation C220 Series Chipset Family H81 Express LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GM107M [GeForce GTX 860M] (rev a2)
01:00.1 Audio device: NVIDIA Corporation Device 0fbc (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
04:00.0 Network controller: Intel Corporation Wireless 3160 (rev 83)
kain@kain-ASM100:~$ 

```

---

### Post by Kuro_Kitsune on 2015-09-06
sorry to double post but as an update to anyone who may ever be looking to get it working as I was. from what I understand from looking all over the HDMI is just a passthrough and does not work like a normal TV-tuner/capture device so the feature is sadly Windows only. Oh well Other then that to anyone looking to install ubuntu on the Alpha Ubuntu 15.04 works great installed drivers and steam and been playing Arma 3 native in linux.

---

