---
title: "Getting Pre-N wireless card to work."
date: 2006-03-31
forum: Hardware &amp; Laptops
---

### Post by Xitanto on 2006-03-31
My Pre-N wireless card isn't working for me. It is fine on Windows, but with the proper NDisWrapper driver installed it still doesn't get detected by the system.

Is there anything else I need for ubuntu to recognise my card? Here's the results of lspci.

```
0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 04)
0000:00:02.0 VGA compatible controller: Intel Corp. Mobile Graphics Controller (rev 04)
0000:00:02.1 Display controller: Intel Corp. Mobile Graphics Controller (rev 04)0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
0000:00:1c.1 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d4)
0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
0000:00:1e.3 Modem: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
0000:05:01.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:05:02.0 Network controller: Broadcom Corporation: Unknown device 4318 (rev 02)
0000:05:04.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)

```

---

### Post by Jason_25 on 2006-03-31
I think it's a complete no-go.  The pre-n features haven't been implemented in ndiswrapper yet.  I would love to have my pre-n cards work with linux.

---

### Post by Xitanto on 2006-03-31
Jason, it's listed on the supported cards list! I'm sure it's another problem. Also, I have a backup 802.11g reciever built into the laptop. Is there any chance of that working? It should be on that list, but I can't see it.

---

### Post by Jason_25 on 2006-03-31
Thanks for the updated info.  I'll try to get mine going soon.  I expect I will have to jump through extra hurdles because mine is in a cardbus PCI slot (belkin f5d8000).

---

