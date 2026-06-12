---
title: "How to make use of Highspeed USB?"
date: 2005-11-19
forum: Hardware &amp; Laptops
---

### Post by itsnotvalid on 2005-11-19
Highspeed USB i.e. USB 2.0

I am wondering why my highspeed USB devices aren't making the desired speed compared to my Windows Box (which the windows box is older)
My chipset is Intel i945, motherboard made by ASUS.

See if any of you could tell me how as I am getting ipod nano this week so I really want to get the full speed.

---

### Post by gmc on 2005-11-19
[QUOTE=itsnotvalid]Highspeed USB i.e. USB 2.0

I am wondering why my highspeed USB devices aren't making the desired speed compared to my Windows Box (which the windows box is older)
My chipset is Intel i945, motherboard made by ASUS.

See if any of you could tell me how as I am getting ipod nano this week so I really want to get the full speed.[/QUOTE]

Interesting you should mention that, I'm finding the same problem with a USBHD drive I just added to my setup. Copying files to and from it are really slow.

When I look at /dev/proc/usb/devices, it reports the following for my USBHD, even though it is a v2.0 device:

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=118/900 us (13%), #Int=  1, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.12-9-686 uhci_hcd
S:  Product=Intel Corporation 82801BA/BAM USB (Hub #1)
S:  SerialNumber=0000:00:1f.2
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

I don't expect it to scream, but copying files back and forth should be faster than what I'm seeing now for a USB v2 device. Could the port be operating at v1.1 speeds?

G.

---

### Post by ubuntolog on 2005-11-22
[QUOTE=gmc]Interesting you should mention that, I'm finding the same problem with a USBHD drive I just added to my setup. Copying files to and from it are really slow.

When I look at /dev/proc/usb/devices, it reports the following for my USBHD, even though it is a v2.0 device:

.....

I don't expect it to scream, but copying files back and forth should be faster than what I'm seeing now for a USB v2 device. Could the port be operating at v1.1 speeds?

G.[/QUOTE]

the same problems on dell gx280 (chipset i915)
but no such troubles with mandriva 2006 installed on same computer

cat /proc/bus/usb/devices

T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8
B:  Alloc=  0/800 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS= 8 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.12-9-686 ehci_hcd
S:  Product=Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
S:  SerialNumber=0000:00:1d.7
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=256ms

T:  Bus=05 Lev=01 Prnt=01 Port=05 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=6737 ProdID=4695 Rev=11.06
S:  Manufacturer=InPrice
S:  Product=IDS-ZIV_UF
S:  SerialNumber=11100E00006B0AC7
C:* #Ifs= 1 Cfg#= 2 Atr=c0 MxPwr= 98mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
E:  Ad=01(O) Atr=02(Bulk) MxPS= 512 Ivl=125us
E:  Ad=82(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=83(I) Atr=03(Int.) MxPS=   2 Ivl=32ms

---

### Post by itsnotvalid on 2005-11-25
That means it is a like a Ubuntu-specific problem with the configs somewhere down the road.
Hope someone could give me a HOWTOs..

---

