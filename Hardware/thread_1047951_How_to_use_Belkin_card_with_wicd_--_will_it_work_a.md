---
title: "How to use Belkin card with wicd -- will it work at all ??"
date: 2009-01-22
forum: Hardware
---

### Post by jerrynewt on 2009-01-22
Sorry I should have posted here first instead of Absolute Beginner Talk.

I am using the built in wifi card in my notebook (specs in signature). I also have a Belkin Wireless G Notebook Network Card that I bought a few months back (can't really remember why though). I am using wicd instead of network manager for wireless connection, but the signal strength is really low -- 15 to 17 percent here in this motel room. My gnome netstatus-applet shows 64 to 65 percent signal strength. I assume the discrepancy is due to the built in wifi not receiving as well as it should. Question is if I turn the built in wifi off and plug in the Belkin will wicd recognize it and how would I go about setting it up without network manager ?? I have tried a few times but no joy as of yet. Wicd shows no wireless networks in range with the card inserted. Any ideas or should I just shut up and deal with the low signal strength ? Thanks for the patience, and responses.

lspci outupt

00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go] (rev a3)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
02:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
02:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
02:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
02:0d.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)
05:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

---

