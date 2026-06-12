---
title: "Wireless LAN on Ubuntu 9.10"
date: 2010-04-03
forum: Hardware
---

### Post by jancok.buntu on 2010-04-03
Need help guys.
I'm using **HP-DV4 1225dx**.. I just installed this **Ubuntu 9.10 (64-bit)**.
The problem is, **i can't use my WirelessLAN**..
Can anybody help me..

---

### Post by Fafler on 2010-04-03
Well, first you need to give us some more information. Open a terminal and type lspci and lsusb and post the output here.

After doing that, try going to System -> Administration - > Hardware Drivers. If theres a 3 rd. party driver available for your system, try using it. Otherwise you might need to download the Windows driver and install it under ndiswrapper.

---

