---
title: "TUSB3410 driver - lots of troubles"
date: 2008-09-17
forum: Hardware
---

### Post by robertuntu on 2008-09-17
Follows cat /proc/bus/sub/device output:

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.18-4-686 ohci_hcd
S:  Product=OHCI Host Controller
S:  SerialNumber=0000:00:02.0
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  4 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=ff(vend.) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=06e0 ProdID=0319 Rev= 1.01
S:  Manufacturer=Texas Instruments
S:  Product=TUSB3410 Serial Port
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=ff(vend.) Sub=00 Prot=00 Driver=(none)
E:  Ad=01(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms

Using linux debian etch, kernel 2.6.18-4-686.

I tried anything but when connect Multitech Multimodem ZBA no drivers was found.

I compiled driver from source on CD (tried also that fron site). Initially no usb-serial.h was found in kernel source (resolved - taken from 2-6-24 kernel source), then many error in ti_usb_3410_5052.c and .h was found, files included in source on CD (resolved - taken that from 2.6.18 kernel source).

ti_usb drivers (module) be present on debian etch, but does not work, so i deleted it and subst with new compiled, i rebooted, but nothing works, always (none) instead of driver !!!

Can you help me ? I must install an hylafax machine with debian and many modem.

As an alternative for the future, can some tell us a modem at low cost compatible with cdc acm that can be installed without all this troubles !

Thak you very much.

---

### Post by DoctorMO on 2008-09-17
I recommend that when compiling kernel models such as these that you not download individual header files from different versions of the kernel.

Instead install the kernel-headers deb package as well as the build-deps for the kernel.

All of this isn't the simplest way of installing a driver however. You might find it less of a trouble to get a modem that doesn't cause these problems.

---

### Post by robertuntu on 2008-09-17
Unfortunately debian etch linux-source-2.6.18 and header 2.6.18 does not contain usb-serial.h !?! I look for a solution very hard but I can't find that. So i solved picking that header file from 2.6.24 headers.

I know... using different hardware avoid me many troubles, but there is not lots of lists of USB modem working with distros/version/kernel (debian/etch/2.6.18 in this case) without problems. furthermore many vendor change chip in their products without evidence of that. I bought some modem from same vendor that changes communication chip: one working well, other with driver sell apart, ....

For the moment my solution is to employ serial-usb converters at low cost coupled with serial modem. I found lot of serial-usb converters working well.

If I can solve problem with serial-usb converter used by MultimodemZBA however, I can use this piece of hardware I bought.

Thank you.

---

### Post by DoctorMO on 2008-09-17
If usb-serial.h is not available in your kernel version then you should upgrade your entire kernel to 2.6.24 not just one file. how you think that this one file will work ok when a header file references an object library binary which will also not be available at run time. Very Bad.

So upgrade kernel and then recompile against new kernel.

---

