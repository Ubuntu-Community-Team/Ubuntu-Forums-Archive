---
title: "Dell touchpad not recognized. Need drivers for 13.04?"
date: 2013-10-06
forum: Hardware
---

### Post by adamitj on 2013-10-06
Hello everyone. I bought a new Dell Inspiron 14 notebook which cames with a touchpad (or mousepad as you name it) but it doesn't works on Xubuntu 13.04 64-bit.

I'm using a external USB mouse to use Ubuntu, but need mousepad for special situations (like when I'm on airport lounges waiting my flight or at shopping cafes eating'n'working).

I had to "hack" my notebook because it cames with Windows 8 and that crap of UEFI and Secure Boot. Ok, after a week I could let it work in dual boot with Windows 8 (still I need it to run some company apps), but this touchpad issue is giving me nuts. So, I did:


- Installed "Touchpad-Indicator". No devices were found;


- The result for ```
lsmod | grep mouse
``` is... nothing!;


- Result for ```
dmesg | grep mouse
``` is:
[    0.759121] mousedev: PS/2 mouse device common for all mice


- I'm loading grub with "acpi=noirq" and also doesn't makes any difference;


- ```
lspci
``` returns this:

```
adamitj@hapsby:~$ lspci
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1c.5 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 6 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
02:00.0 VGA compatible controller: NVIDIA Corporation GK107M [GeForce GT 730M] (rev a1)
06:00.0 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
```


Probably it's lacking some drivers, but can't find them. Does anyone knows if exists a Linux driver for my Dell touchpad? On Dell support site there is nothing about...

---

### Post by varunendra on 2013-10-07
Please post back the outputs of -
```
xinput
lsmod
cat /proc/bus/input/devices
```

And have you tried booting without the acpi=noirq option?

---

### Post by adamitj on 2013-10-07
Solved by installing Ubuntu 13.04 then Xubuntu package... don't know what was the problem since I needed to use it. Thank you!

---

