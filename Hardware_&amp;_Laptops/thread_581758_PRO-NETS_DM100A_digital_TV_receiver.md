---
title: "PRO-NETS DM100A digital TV receiver"
date: 2007-10-19
forum: Hardware &amp; Laptops
---

### Post by Limulf on 2007-10-19
Hello. I have been trying to make this TV receiver work on my notebook in Ubuntu 7.10, to no avail. I can't find the correct module to load, nor which parameters should I use. It works on Windows XP with a driver in a CD I got with the computer, though.

 The card's specifications can be found [here]("http://www.pro-nets.com/eng/product.php?mode=show&cid=109&pid=143").

And this is my lspci output:
```
thorin@Moria:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
01:04.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
01:04.2 Generic system peripheral [0805]: O2 Micro, Inc. Integrated MMC/SD Controller (rev 01)
01:04.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
08:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
thorin@Moria:~$ 

```.

 Thanks for your time.

---

### Post by Limulf on 2008-02-22
Hello again. Finally, I made the card work, with the driver for the Afatech AF9015 chip made by the nice people at [LinuxTV]("http://www.linuxtv.org/"). First, I got a firmware file and the driver from [here]("http://www.linuxtv.org/wiki/index.php/Afatech_AF9015"); and then followed [these instructions]("http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers"). The only downside is that I have to select and launch the channel I want to see from the console, but it is not a big deal.

 Sorry about the "post necromancy", but I thought it would be a good idea to write this; just in case someone else encounters the same problem.

 Best regards.

---

