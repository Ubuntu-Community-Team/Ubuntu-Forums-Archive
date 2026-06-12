---
title: "Tatung Elio 810 photo jukebox"
date: 2006-12-31
forum: Hardware &amp; Laptops
---

### Post by MrCheese on 2006-12-31
I recently bought a Tatung Elio 810 mp3 player/photo jukebox on eBay - it works great & was a real bargain. Hpowever I can't get Ubuntu (Dapper) to access it beyond the initial device probe, not even as a USB hard drive. I installed Gnomad2 & libmtp, both of which fail to find the device.

When I plug the player in I get the following :
usb 5-8: new high speed USB device using ehci_hcd and address 10

cat /proc/bus/usb/devices :

T:  Bus=05 Lev=01 Prnt=01 Port=07 Cnt=03 Dev#= 10 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1460 ProdID=2126 Rev= 0.01
S:  Manufacturer=Tatung Co.
S:  Product=elio Photo Jukebox P810
S:  SerialNumber=1f00045a-00100000-02007e00-007a003f-00001000
C:* #Ifs= 1 Cfg#=128 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=01(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=82(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=81(I) Atr=03(Int.) MxPS= 512 Ivl=1ms

so the system can at least see the hardware even if it doesn't know what to do with it.

Can anybody point me in the right direction to get this running?  I don't really want to have to boot XP just to access my mp3 player :0(

---

