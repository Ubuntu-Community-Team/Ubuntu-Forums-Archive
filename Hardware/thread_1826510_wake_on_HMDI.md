---
title: "wake on HMDI"
date: 2011-08-16
forum: Hardware
---

### Post by hdmiwake on 2011-08-16
so i know its possible to redirect certian inputs to wake the computer such as usb and line in using cat XXX > /proc/acpi/wakeup. and i know hdmi tells the computer wether it is active or not(unlike vga) so i was wondering if it would be possible to wake the computer when the monitor was turned on ? 

here is the output of 
cat /proc/acpi/wakeup

```

[LIST=1]
[*]Device  S-state   Status   Sysfs node
[*]P0P1      S4     disabled  pci:0000:00:1e.0
[*]USB2      S3     disabled  pci:0000:00:1d.2
[*]USB3      S4     disabled  pci:0000:00:1a.0
[*]USB5      S4     disabled  pci:0000:00:1a.2
[*]HDEF      S4     disabled  pci:0000:00:1b.0
[*]RP04      S4     disabled  pci:0000:00:1c.3
[/LIST]

```and here is the output of lspci

```

[LIST=1]
[*]00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
[*]00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
[*]00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
[*]00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
[*]00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
[*]00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
[*]00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
[*]00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
[*]00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
[*]00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
[*]00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
[*]00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
[*]00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
[*]00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
[*]00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
[*]00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
[*]00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
[*]00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
[*]00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
[*]04:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)
[*]05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
[/LIST]

```

---

### Post by hdmiwake on 2011-08-17
so i found this thread which mght be helpful 
[http://ubuntuforums.org/showthread.php?t=814939&page=1](http://ubuntuforums.org/showthread.php?t=814939&page=1)

does anyone have an idea which lspci output refers to the hdmi port?

---

### Post by hdmiwake on 2011-08-17
anyone?

---

