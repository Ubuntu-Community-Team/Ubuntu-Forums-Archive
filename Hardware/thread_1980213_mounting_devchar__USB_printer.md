---
title: "mounting /dev/char  USB printer"
date: 2012-05-14
forum: Hardware
---

### Post by Silvernail on 2012-05-14
Oneiric
Gnome3

I would like to create a path to the charecter device listed below so I can access it with a script.  I can find this printer all over the place. Just can not find where/how to mount a char device. I see no mention of link so I haven't tried that yet.

My print apts can find it and print to it.
Any help would be appreciated.
Dave


> /dev/char/
lrwxrwxrwx 1 root root 18 2012-05-14 17:04 189:4 -> ../bus/usb/001/005

> lsusb
Bus 001 Device 005: ID 040a:4026 Kodak Co.
> usb-devices
T:  Bus=01 Lev=01 Prnt=01 Port=04 Cnt=03 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=040a ProdID=4026 Rev=00.01
S:  Manufacturer=Eastman Kodak Company
S:  Product=KODAK 5300 AiO
S:  SerialNumber=B7AI3204
C:  #Ifs= 3 Cfg#= 1 Atr=c0 MxPwr=2mA
I:  If#= 0 Alt= 0 #EPs= 5 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 2 Cls=07(print) Sub=01 Prot=02 Driver=(none)
I:  If#= 2 Alt= 0 #EPs= 3 Cls=06(still) Sub=01 Prot=01 Driver=(none)

> 
dave@dave:/dev/char$ udevadm info --query=all --name=/dev/bus/usb/001/005
P: /devices/pci0000:00/0000:00:1d.7/usb1/1-5
N: bus/usb/001/005
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb1/1-5
E: MAJOR=189
E: MINOR=4
E: DEVNAME=/dev/bus/usb/001/005
E: DEVTYPE=usb_device
E: DRIVER=usb
E: PRODUCT=40a/4026/1
E: TYPE=0/0/0
E: BUSNUM=001
E: DEVNUM=005
E: SUBSYSTEM=usb
E: ID_VENDOR=Eastman_Kodak_Company
E: ID_VENDOR_ENC=Eastman\x20Kodak\x20Company
E: ID_VENDOR_ID=040a
E: ID_MODEL=KODAK_5300_AiO
E: ID_MODEL_ENC=KODAK\x205300\x20AiO
E: ID_MODEL_ID=4026
E: ID_REVISION=0001
E: ID_SERIAL=Eastman_Kodak_Company_KODAK_5300_AiO_B7AI3204
E: ID_SERIAL_SHORT=B7AI3204
E: ID_BUS=usb
E: ID_USB_INTERFACES=:ffffff:070102:060101:
E: ID_GPHOTO2=1
E: GPHOTO2_DRIVER=PTP
E: COLORD_DEVICE=1
E: COLORD_KIND=camera
E: TAGS=:udev-acl:


---

