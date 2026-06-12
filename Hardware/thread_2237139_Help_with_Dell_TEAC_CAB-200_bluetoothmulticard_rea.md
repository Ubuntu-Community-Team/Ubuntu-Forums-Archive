---
title: "Help with Dell TEAC CAB-200 bluetooth/multicard reader"
date: 2014-07-30
forum: Hardware
---

### Post by zero-cool74205 on 2014-07-30
I am using Ubuntu 14.04 and I can not get it to recognize my bluetooth adapter. I know the computer can use the adapter because my keyboard is working,but Ubuntu tells me I have no adapters and so I can not connect anything else. I have tried using hid2hci which just keeps timing out. I'm at a complete loss and google has not helped. Any suggestions would be great. I should mention that I've only been running linux for a couple of months, I am capable but in no way an expert.

This is what shows up in 'usb-devices'
T:  Bus=01 Lev=01 Prnt=01 Port=03 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0644 ProdID=0201 Rev=07.12
S:  Manufacturer=DELL
S:  Product=CAB-200
S:  SerialNumber=000001178131
C:  #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=98mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

---

### Post by Vladlenin5000 on 2014-07-31
Are you sure your (wireless, supposedly) keyboard is Bluetooth? Many wireless keyboard out there aren't Blutooth. They use a proprietary and dedicated USB receiver, a simple RF one that in spite of using the same frequency of Bluetooth (and WiFi, and cordless phones, and microwave ovens, and...) it ISN'T therefore they only work with the product they were made for...

---

### Post by zero-cool74205 on 2014-07-31
I am positive. Number one the power indicator on the keyboard has the bluetooth rune, number two it connects to the CAB-200 that I'm having problems with, and number three the cab-200 is how I connected bluetooth devices in windows. When I cut the power to the CAB-200 the keyboard no longer works, so I know it's not connecting some other way.

---

