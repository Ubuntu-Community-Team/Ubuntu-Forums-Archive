---
title: "PCI says no drivers"
date: 2010-12-01
forum: Hardware
---

### Post by tembo on 2010-12-01
i was using linux mint when one day my usb wasnt being detected when i plugged it in, then the wireless internet wasn't working; it just simply looks as if i've disabled the wireless

in the terminal, iwconfig gives;

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bgn  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.422 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   
          Retry: on   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



Debian HCL ([http://kmuto.jp/debian/hcl/index.rhtmlx](http://kmuto.jp/debian/hcl/index.rhtmlx)) gives me this

80862a40YesIntel CorporationMobile 4 Series Chipset Memory Controller Hubintel-agp
      80862a42YesIntel CorporationMobile 4 Series Chipset Integrated Graphics Controlleri915v2.6.32-       80862a43
Intel CorporationMobile 4 Series Chipset Integrated Graphics Controller

      80862937
Intel Corporation82801I (ICH9 Family) USB UHCI Controller #4

      80862938
Intel Corporation82801I (ICH9 Family) USB UHCI Controller #5

      80862939
Intel Corporation82801I (ICH9 Family) USB UHCI Controller #6

      8086293c
Intel Corporation82801I (ICH9 Family) USB2 EHCI Controller #2

      8086293eYesIntel Corporation82801I (ICH9 Family) HD Audio Controllersnd-hda-intelv2.6.25-       80862940
Intel Corporation82801I (ICH9 Family) PCI Express Port 1

      80862942
Intel Corporation82801I (ICH9 Family) PCI Express Port 2

      80862946
Intel Corporation82801I (ICH9 Family) PCI Express Port 4

      80862934
Intel Corporation82801I (ICH9 Family) USB UHCI Controller #1

      80862935
Intel Corporation82801I (ICH9 Family) USB UHCI Controller #2

      80862936
Intel Corporation82801I (ICH9 Family) USB UHCI Controller #3

      8086293a
Intel Corporation82801I (ICH9 Family) USB2 EHCI Controller #1

      80862448YesIntel Corporation82801 Mobile PCI Bridgei810_rng
      80862917YesIntel CorporationICH9M-E LPC Interface ControlleriTCO_wdtv2.6.28-       80862929YesIntel CorporationICH9M/M-E SATA AHCI Controllerahciv2.6.25-       80862930YesIntel Corporation82801I (ICH9 Family) SMBus Controlleri2c-i801v2.6.25-       10ec8172
Realtek Semiconductor Co., Ltd.RTL8191SEvB Wireless LAN Controller

      10ec8136YesRealtek Semiconductor Co., Ltd.RTL8101E/RTL8102E PCI Express Fast Ethernet controllerr8169v2.6.25-
how do i fix this?

regards

---

