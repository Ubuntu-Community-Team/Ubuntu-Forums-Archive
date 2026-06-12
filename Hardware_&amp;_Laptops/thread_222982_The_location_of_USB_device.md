---
title: "The location of USB device"
date: 2006-07-25
forum: Hardware &amp; Laptops
---

### Post by Asix on 2006-07-25
I'm running Kubuntu 6.06 and I would like to utilize my USB ISDN adapter so I can connect to the Internet on Kubuntu.
When I plug my adapter into one USB port, and when I run the command:
```
cat /etc/dev
```
and when I find the information corresponding my modem, I get the following output:
```
T:  Bus=03 Lev=01 Prnt=01 Port=01 Cnt=02 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=02(comm.) Sub=00 Prot=00 MxPS=16 #Cfgs=  1
P:  Vendor=0bf1 ProdID=0002 Rev= 1.00
S:  Manufacturer=Intracom S.A.
S:  Product=NetMod USB
S:  SerialNumber=Firmware Ver 1.0
C:* #Ifs= 2 Cfg#= 1 Atr=60 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=02(comm.) Sub=02 Prot=01 Driver=cdc_acm
E:  Ad=81(I) Atr=03(Int.) MxPS=  16 Ivl=10ms
I:  If#= 1 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm
E:  Ad=82(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
```
I would like to know where this device is located in system settings (which tty device), so I can enter the correct information in kppd when setting up my modem. Is it possible to find out that sort of information with this command?

---

### Post by zxee on 2006-07-26
Since it's a usb device try lsusb. I don't know if that will give you the tty address or not but it's worth trying. And here's a thread [http://mybroadband.co.za/vb/showthread.php?t=21726&page=20](http://mybroadband.co.za/vb/showthread.php?t=21726&page=20) 
that seems related to the usb-ttyS issue-hope that helps.

---

