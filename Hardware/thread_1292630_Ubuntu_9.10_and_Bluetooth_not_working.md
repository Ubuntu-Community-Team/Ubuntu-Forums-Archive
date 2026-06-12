---
title: "Ubuntu 9.10 and Bluetooth not working"
date: 2009-10-16
forum: Hardware
---

### Post by mateom on 2009-10-16
Hi,

I have just installed Ubuntu 9.10 on my new Toshiba Satellite U400-177. The laptop manufacturer says I have a Bluetooth adapter bundled with it, but I am not able to make it works. Gnome-bluetooth says I have not any bluetooth adapters on my computer.

I don't know what adapter is bundled with the laptop. Lspci and lsusb doesn't give any information about bluetooth adapters, so I guess the bluetooth adapter is included in the WiFi card, wich is an "Intel Corporation Wireless WiFi Link 5100" card.

Outputs of lsusb and lspic are:

```
mateo@pluto:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 04f2:b008 Chicony Electronics Co., Ltd USB 2.0 Camera
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 046d:c51b Logitech, Inc. V220 Cordless Optical Mouse for Notebooks
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


mateo@pluto:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
07:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040T PCI-E Fast Ethernet Controller (rev 12)
08:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
0a:01.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
0a:01.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
0a:01.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
```I have missed something?

Thanks in advance.

PS: I didn't test if bluetooth works with other GNU/Linux distros.

---

### Post by mateom on 2010-09-09
Toshiba uses it's own Bluetooth stack and provides drivers for Windows only, as usual. And, as usual too, the community reverse engineered the drivers and now are available on the latest GNU/Linux kernels.

If you are using an old kernel, you can enable the Bluetooth executing the command 

```
sudo toshset -bluetooth on
```You may need to patch your kernel if you get the message "required kernel toshiba support not enabled.". In this case, post on this thread and I may help you in the process or search in google for the patch (very easy to find).

But if you are using an Ubuntu version greater than 10.04 (I thought that from this version the ubuntu shipped kernel came with toshiba support) you can't use toshset. Instead, you only need to execute:

```
sudo echo "options omnibook ectype=14 bluetooth=1" > /etc/modprobe.d/omnibook.conf
```Reboot your system and bluetooth should work. If it doesn't, try changing the parameter ectype from 10 to 15.

---

