---
title: "Hauppauge DualHD ATSC tuner not being recognized"
date: 2019-09-10
forum: Hardware
---

### Post by Benjamin_Z on 2019-09-10
I have a DIrectTV local channel connector tuner that I am trying to get working under Linux. The DirectTV tuner is essentially a re-branded Hauppauge DualHD ATSC tuner. The tuner works perfectly under Windows when forcing it to use the Hauppauge DualHD ATSC driver. However, I can not get it working on Ubuntu at all. I have tried on various Ubuntu distros(Lubuntu 16.04, Linux Mint 19.2, and Ubuntu 18.04(both physcial install and virtualmachine)) on various diffrent laptops with no luck in any of them. In all instances I followed the directions on the website for the PPA and it seemed to install fine with no errors. However when i plug in the device no such luck as it being recognized under usb-devices nor dmesg. It just appears as 

[    1.691490] usb 1-1: New USB device found, idVendor=eb1a, idProduct=5902, bcdDevice= 1.00
[    1.691491] usb 1-1: New USB device strings: Mfr=0, Product=1, SerialNumber=2
[    1.691492] usb 1-1: Product: USB ATSC Device
[    1.691493] usb 1-1: SerialNumber: 0


and 

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=eb1a ProdID=5902 Rev=01.00
S:  Product=USB ATSC Device
S:  SerialNumber=0
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=300mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=00 Prot=00 Driver=(none)


I believe the error lies within the tuner not being recognized as a Hauppauge causing the correct drivers not to load. Maybe I need to somehow tell the drivers to load for this device? Does anyone have any ideas or suggestions on where the problem may lie and how to fix it?  Any help and suggestions are welcome!

---

