---
title: "Another Wireless Setup Question"
date: 2005-12-31
forum: Hardware &amp; Laptops
---

### Post by Wuhu on 2005-12-31
Hi all, sorry for yet another question on how to set up a wireless card on Ubuntu, but I'm stumped and I can't find the solutions on the forum.  I've downloaded and installed all the Ndiswrapper and Ndisgtk tools, installed my Windows wireless drivers, and tried to connect to a network with zero luck.  Ubuntu tells me no hardware is present even though the PCMCIA network card is installed.  

I'm using a Hawking card with RT2500 chipset.  Have I somehow disabled my hardware? :(

---

### Post by vasudevank on 2005-12-31
try lspci and see if your card is there, what about iwconfig please poset what you get do you need any modules that were not loaded?

---

### Post by Wuhu on 2006-01-03
Sorry for the delay.  Here's the lspci and iwconfig.  It lists the card (it appears), but still no joy on getting it to work:

0000:00:00.0 Host bridge: Intel Corp. 82815 815 Chipset Host Bridge and Memory C ontroller Hub (rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 82815 815 Chipset AGP Bridge (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 02)
0000:00:1f.0 ISA bridge: Intel Corp. 82801BAM ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801BAM IDE U100 (rev 02)
0000:00:1f.2 USB Controller: Intel Corp. 82801BA/BAM USB (Hub #1) (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 Go] (r ev b2)
0000:02:03.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
0000:02:06.0 Communication controller: Lucent Microelectronics WinModem 56k (rev  01)
0000:02:0f.0 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controlle r
0000:02:0f.1 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controlle r
0000:02:0f.2 FireWire (IEEE 1394): Texas Instruments PCI4451 IEEE-1394 Controlle r
0000:03:00.0 Network controller: RaLink Ralink RT2500 802.11 Cardbus Reference C ard (rev 01)

lo        no wireless extensions.

ra0       RT2500 Wireless  ESSID:""
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-120 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

Any help is much appreciated.

---

