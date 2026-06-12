---
title: "Wireless connection not working"
date: 2011-12-29
forum: Hardware
---

### Post by pauloz on 2011-12-29
Greetings!

I've recently installed Ubuntu 10.04 on to a friend's Acer Aspire 3500. Yes I know it's got whiskers but Ubuntu has given the laptop a new lease of life and hopefully a few more months, maybe a year or two, out of it.

I suspect there may be an issue with the wireless card in the laptop - it did work for a while but now the laptop won't connect to my wireless network. Presently, the "Enable Wireless" option is greyed out - wired it works fine. Is there any testing or modification to settings that I can do that will confirm a problem with the wireless card?

Thanks!

---

### Post by psycho5 on 2011-12-30
Google the laptop model and see what is the default wifi driver that the laptop uses. The make and model. Then go to terminal and type 

```
lspci
``` 

press enter and paste the output here, that would be a start. It should show what driver is ubuntu using (if the wifi is actually being detected). 

Also, if it's a fresh install, I might recommend installing 11.04 using the live cd instead of 10.04. Plug in the LAN cable during the live cd installation, let it download all updates, etc. It should tell you hardware restricted drivers available. That would be an easy solution. But I'm not sure how old the laptop is.

---

### Post by garnet_xtian on 2011-12-30
> **psycho5 said:**
> Google the laptop model and see what is the default wifi driver that the laptop uses. The make and model. Then go to terminal and type 

```
lspci
```press enter and paste the output here, that would be a start. It should show what driver is ubuntu using (if the wifi is actually being detected). 

Also, if it's a fresh install, I might recommend installing 11.04 using the live cd instead of 10.04. Plug in the LAN cable during the live cd installation, let it download all updates, etc. It should tell you hardware restricted drivers available. That would be an easy solution. But I'm not sure how old the laptop is.


chris@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)
chris@ubuntu:~$

the desktop was freeze up after enabled the hardwared. please help me here!:(

---

### Post by pauloz on 2012-01-02
> **psycho5 said:**
> Google the laptop model and see what is the default wifi driver that the laptop uses. The make and model. Then go to terminal and type 

```
lspci
``` 

press enter and paste the output here, that would be a start. It should show what driver is ubuntu using (if the wifi is actually being detected). 

Also, if it's a fresh install, I might recommend installing 11.04 using the live cd instead of 10.04. Plug in the LAN cable during the live cd installation, let it download all updates, etc. It should tell you hardware restricted drivers available. That would be an easy solution. But I'm not sure how old the laptop is.
Unfortunately, I don't have the laptop anymore and I'm not sure when I'll get it back. My friend will connect with Ethernet for the time being.
Thanks for your reply.

---

