---
title: "Sony Vaio SVE1112 Brightness Control doesn't work"
date: 2012-12-25
forum: Hardware
---

### Post by micdhack on 2012-12-25
I am having a problem that many sony users have with the brightness control not working. I've tried to add acpi_brightness=video in /etc/default/grub and sudo update-grub but didn't work. I have also tried echo NUM > /sys/....brightness but that too didn't work..no effect whatsoever.

The only thing that I couldn't do was the xorg.conf file fix because i have no xorg.conf file.

Can you help me? I am out of ideas. Here is my lspci in case it helps.

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Device 9808
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Wrestler HDMI Audio [Radeon HD 6250/6310]
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Port
00:05.0 PCI bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Port
00:06.0 PCI bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Port
00:07.0 PCI bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Port
00:10.0 USB controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03)
00:11.0 SATA controller: Advanced Micro Devices [AMD] Hudson SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices [AMD] Hudson SMBus Controller (rev 14)
00:14.2 Audio device: Advanced Micro Devices [AMD] Hudson Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] Hudson LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] Hudson PCI Bridge (rev 40)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 07)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
03:00.0 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev 01)

```

---

### Post by Toz on 2012-12-30
> I've tried to add acpi_brightness=video in /etc/default/grub
The parameter is actually **acpi_backlight=vendor**

If that doesn't work, try **acpi_osi=**

You can verify that the parameter is successfully being used by issuing the following command:
```
cat /proc/cmdline
```

Can you also post back more detailed info about your video card and the driver being used:
```
sudo lspci -vnn | grep -A12 VGA
```

And what version of Ubuntu are you using?

EDIT: This might be of value: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1093795]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1093795").

---

