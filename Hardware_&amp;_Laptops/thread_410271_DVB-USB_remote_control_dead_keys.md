---
title: "DVB-USB remote control: dead keys"
date: 2007-04-15
forum: Hardware &amp; Laptops
---

### Post by pljones on 2007-04-15
Hi,

I've searched high and low for help on this with no luck.  I've got a USB DVB-T receiver with remote control.  All works fine apart from two keys on the remote (ChUp and Vol+).  I've been completely unable to track down where the keymap is defined, however!

The /proc/bus/usb/devices entry looks like this:
```
T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0db0 ProdID=5581 Rev= 1.02
S:  Manufacturer=PC-DTV Receiver
S:  Product=PC-DTV Receiver
S:  SerialNumber=00000001
C:* #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=00 Prot=00 Driver=dvb_usb_gl861
E:  Ad=81(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
I:  If#= 0 Alt= 1 #EPs= 2 Cls=ff(vend.) Sub=00 Prot=00 Driver=dvb_usb_gl861
E:  Ad=81(I) Atr=01(Isoc) MxPS=3072 Ivl=125us
E:  Ad=02(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=01 Driver=usbhid
E:  Ad=83(I) Atr=03(Int.) MxPS=  64 Ivl=2ms
```
It's got a "usbhid" standard HID device entry.  What I suppose I'm looking for, then, is how to configure the "dead" keys.

On a related note, my HP-2501 keyboard generates the following kernel messages for otherwise "dead" keys:
```
Apr 15 17:53:21 thermaltake kernel: [15959.319647] atkbd.c: Use 'setkeycodes e023 <keycode>' to make it known.
Apr 15 17:53:21 thermaltake kernel: [15959.393840] atkbd.c: Unknown key released (translated set 2, code 0xa3 on isa0060/serio0).
```
Is "setkeycodes" the right way to **permanently** fix this?  What do I do for X?

Thanks for *any* help! :)

---

### Post by awilkins on 2007-11-21
The keymaps are defined in the driver source, which is in the kernel sources. I can't tell you which map your device uses, but the keymaps are in 

drivers/media/common/ir-keymaps.c

You do need to be experienced enough to build and install a custom kernel (or at least the kernel modules) to be able to resolve this.

They are pretty simple - there is just an array for each one. If you do fix it up, please submit your changes as a patch to the kernel mailing list.

---

### Post by pljones on 2007-11-23
Thanks -- I've not built an Ubuntu-packaged kernel before.  (I've spent many a long evening building kernels, though, way back to 1.0.x days!  There's a lot more in a build since then........)  I'll take a look at the source and see if I can make head-or-tail of it enough to delve in.

---

### Post by pljones on 2007-11-23
The remote control is appearing as a USB keyboard:
```
input: USB HID v1.01 Keyboard [PC-DTV Receiver PC-DTV Receiver]
```
input-kbd says:
```
/dev/input/event2
   bustype : BUS_USB
   vendor  : 0xdb0
   product : 0x5581
   version : 257
   name    : "PC-DTV Receiver PC-DTV Receiver"
   phys    : "usb-0000:00:02.2-1/input1"
   uniq    : "00000001"
   bits ev : EV_SYN EV_KEY EV_REP

map: 1 keys, size: 1/64
0x0000 =  30  # KEY_A
```I'm not sure why it stops after one key!  (For my "real" keyboard (no longer the HP-2501), it dumps the whole lot.)  I'm back to being stumped.

---

