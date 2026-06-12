---
title: "Losing Wireless Connection"
date: 2012-01-02
forum: Hardware
---

### Post by xedth2 on 2012-01-02
I've had this issue on two separate machines.  I'll be surfing the internet, then I'll all of a sudden I'll lose my connection to my route.  GNOME wireless applet says I'm still connected and when I check ifconfig I still have an IP.  But when I try and ping my router it says "Destination Host Unreachable".  I'm having this issue on a Toshiba L670 and a Toshiba NB505.  Sometimes I can disconnect and reconnect and get it working but it only fixes it for a moment.  Other times it won't reconnect.  I try bringing the wireless card down, ifconfig eth1 down, and then back up but that works sometimes.  Anybody know why or how to fix this.  This is getting seriously frustrating.  There are two other Ubuntu machines in the house and I haven't seen them having this issue.  And on the Toshiba L670 in Windows I'm not having this issue.  Please help, I have to go back to school in about two weeks and this has to be fixed by then.

Thanks

---

### Post by librechick on 2012-01-03
> **xedth2 said:**
> I've had this issue on two separate machines.  I'll be surfing the internet, then I'll all of a sudden I'll lose my connection to my route.  GNOME wireless applet says I'm still connected and when I check ifconfig I still have an IP.  But when I try and ping my router it says "Destination Host Unreachable".  I'm having this issue on a Toshiba L670 and a Toshiba NB505.  Sometimes I can disconnect and reconnect and get it working but it only fixes it for a moment.  Other times it won't reconnect.  I try bringing the wireless card down, ifconfig eth1 down, and then back up but that works sometimes.  Anybody know why or how to fix this.  This is getting seriously frustrating.  There are two other Ubuntu machines in the house and I haven't seen them having this issue.  And on the Toshiba L670 in Windows I'm not having this issue.  Please help, I have to go back to school in about two weeks and this has to be fixed by then.

Thanks

Run lspci and paste the results here. We need to know what the wifi card is. 802.11N also may be a problem. Not all 802.11N devices work flawlessly together. With some of the free software supported wifi cards there have been fixes to work around some of the problematic routers though.

The verizon myfi routers are a particular problem. This isn't a problem specific to Ubuntu or GNU/Linux. I have encountered these issues in Microsoft Windows too. I don't actually use Microsoft Windows. It was a friends computer.

---

### Post by xedth2 on 2012-01-03
Here's the out put from lspci


00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
07:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)

---

### Post by librechick on 2012-01-08
I would suggest replacing the wifi card. I don't like non-free drivers/firmwre. They are always a problem and that card is dependent on them. I doubt anything else will fix it. You might try booting a live cd though first and just verify it is not a software problem. Get one with an Atheros chipset based cards if you replace the internal card. Or a USB card with RTL8187L or RTL8187B. The atheros PCIe and PCI cards for laptops are easier to find. The USB ones are harder. In any case problem solved 2-3 days. [http://www.thinkpenguin.com/](http://www.thinkpenguin.com/) has all these.

---

