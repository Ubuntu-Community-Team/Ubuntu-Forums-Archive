---
title: "Microsoft Basic Optical Mouse in Edgy"
date: 2006-11-18
forum: Hardware &amp; Laptops
---

### Post by GothicX on 2006-11-18
Hi!

Anyone has a "Microsoft Basic Optical Mouse" working in Edgy?

I've these configuration.. and connected at USB.

Section "InputDevice"
        Identifier      "USB Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
EndSection

I really don't understand why it goes crazy sometimes, or using Gedit and do automatically paste in random lines for example.

T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=045e ProdID=0084 Rev= 0.00
S:  Manufacturer=Microsoft
S:  Product=Basic Optical Mouse
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   4 Ivl=10ms

---

I: Bus=0003 Vendor=045e Product=0084 Version=0000
N: Name="Microsoft Basic Optical Mouse"
P: Phys=usb-0000:00:11.2-2/input0
S: Sysfs=/class/input/input2
H: Handlers=mouse0 event2 ts0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103


I've already tried IMPS/2 protocol, it's the same :-(

Thanks!

---

