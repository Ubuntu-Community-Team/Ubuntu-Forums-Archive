---
title: "No USB after this mornings Ext2 updates"
date: 2007-12-08
forum: Hardware &amp; Laptops
---

### Post by AClark on 2007-12-08
Anybody else having problems with USB after this mornings updates ?

Both my built-in USB 1.1 and a 2.0 PC Card are suddenly dead.  USB Mouse and all of my flash drives are not recognised.

Rebooting doesn't help.

Everything worked yesterday and the only thing I have done today is install the updates that showed up this morning.  If my memory is correct they were related to the Ext2 filesystem.

lsusb yields:
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

lspci yields:
00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #2) (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #3) (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 80)
02:00.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 80)
02:02.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
07:00.0 USB Controller: NEC Corporation USB (rev 41)
07:00.1 USB Controller: NEC Corporation USB (rev 41)
07:00.2 USB Controller: NEC Corporation USB 2.0 (rev 02)


Device manager shows three usb hubs including a 2.0 hub

This is on a Thinkpad A31 with Fiesty

Any ideas ?

I just remembered there was one more thing I did on this computer today.

I bought a D-Link WUA-1340 802.11g USB adapter from NewEgg because reviews indicated that it worked in Ubuntu and it was on sale for $4.99.  

I am setting a T40 up with Gutsy for a friend and it doesn't have built in WIFi.  I figured for 5 bucks and free shipping it was worth a shot even though
 it got generally poor reviews from Windows users.  

I was so pleased when it worked perfectly in the T40 that I tried it in the A31.  This computer has built in WiFi but it is 802.11B and I have had difficulty getting any 
external adapter to work.  Same problems with this one.  It showed up in the network manager but was unable to connect to my open network.

I unplugged it and returned to the T40 where it again worked with no problems.  Shortly after that I wanted a file from the A31 and plugged in a flash drive to copy
it over.  That was when I discovered that USB was no longer working so I guess it is not related to the updates.

After installing the updates I downloaded a couple of podcasts and listened to them while I made breakfast and that is all the activity on this computer today so at this 
point I am baffled.

---

