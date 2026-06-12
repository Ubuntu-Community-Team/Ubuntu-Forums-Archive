---
title: "Mobile broadband will not show/work"
date: 2013-05-03
forum: Hardware
---

### Post by Not unique on 2013-05-03
My Mobile broadband will not show/work can any one please he lp me get internet I attach details thank you.

j@j-PC:~$ lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 01)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Redwood [Radeon HD 5670]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Redwood HDMI Audio [Radeon HD 5000 Series]
02:00.0 Ethernet controller: Atheros Communications Inc. AR8131 Gigabit Ethernet (rev c0)


j@j-PC:~$ lsusb
Bus 001 Device 002: ID 0bc2:0503 Seagate RSS LLC 
Bus 001 Device 004: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E230/E270/E870 HSDPA/HSUPA Modem
Bus 001 Device 006: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 002: ID 03f0:0024 Hewlett-Packard KU-0316 Keyboard
Bus 003 Device 002: ID 1bcf:05ca Sunplus Innovation Technology Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
j@j-PC:~$

---

### Post by Not unique on 2013-05-03
Just installed Huawei Linux driver but no joy

---

### Post by Not unique on 2013-05-03
[COLOR=#222222][FONT=Times New Roman]Just installed Huawei Linux driver but no joy[/FONT][/COLOR]

---

### Post by CatKiller on 2013-05-03
When I was doing similar it showed up as a wired connection. Don't know why. I didn't have to install anything.

I can't remember the model number so I don't know if it's the same as you're using. Same make, though.

EDIT: If you are still using 10.10, you may need to install a package called usb-modeswitch or similar.

---

### Post by Not unique on 2013-05-03
Thanks will try

---

### Post by Not unique on 2013-05-03
No good! but now know that ubuntu Mobile broadband executable is missing

---

### Post by Not unique on 2013-05-04
Does anyone know where I can aquire a ubuntu Mobile broadband executable if that may help??

---

### Post by CatKiller on 2013-05-04
> **Not unique said:**
> Does anyone know where I can aquire a ubuntu Mobile broadband executable if that may help??

This phrase makes no sense. Where did you read it, or otherwise come to the conclusion that this is what you need?

---

### Post by Not unique on 2013-05-04
Came up on error message

---

### Post by CatKiller on 2013-05-04
What error message? What were you doing?

It's like pulling teeth.

---

### Post by Not unique on 2013-05-04
When ubuntu starts or when I try using mobile broadband a error report appears + when I bring up details one line says ubuntu Mobile broadband executable is missing

---

### Post by Not unique on 2013-05-04
Sorry modem manager at /sbin/modem manager is missing

---

### Post by Not unique on 2013-05-05
Sick of it too many times now so moved to Linux mint (temp hopefully).

---

