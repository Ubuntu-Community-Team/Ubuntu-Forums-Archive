---
title: "Laptop lid issues."
date: 2010-02-13
forum: Hardware
---

### Post by Luisnux on 2010-02-13
Ok, I'm having issues when I close the laptop lid on my dell d610 running Ubuntu 9.10.  I've already tried to change the power options but it still did not fix the issue.  So far everything that I know about works on my system but closing the laptop.  The default was set to suspend but then I changed it to hibernate hoping that it would fix it but no luck.  Just in case this might help I'm posting the info from lspci:



00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
03:01.0 CardBus bridge: Texas Instruments PCI6515 Cardbus Controller
03:01.5 Communication controller: Texas Instruments PCI6515 SmartCard Controller
03:03.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)


Thanks in advance for your help.

---

### Post by pizza-is-good on 2010-02-13
What happens when you set it to do nothing upon lid closing?

---

### Post by Luisnux on 2010-02-14
Thanks, you're a genious since that actually worked.  I just set it to blank screen.  However I'm still wondering if there's a way to fix this issue-the world may never find out :).  I mean if there's actually a way to more allow it to go into hibernate/suspend without doing that.  I had the same issue with Mandriva, but it was a lot easier to fix.

---

