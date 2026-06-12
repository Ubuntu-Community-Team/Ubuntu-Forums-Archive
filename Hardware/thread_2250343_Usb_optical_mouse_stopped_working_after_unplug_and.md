---
title: "Usb optical mouse stopped working after unplug and re-plug on ubuntu 14.04lts"
date: 2014-10-28
forum: Hardware
---

### Post by chitzinwin on 2014-10-28
My usb mouse suddenly stopped working without doing any things wrong.

When I tried to check using ---->   *dmesg | grep usb*
the last four lines are as followed

[B][  271.697549] usb 2-1.1: new low-speed USB device number 6 using ehci-pci
[  271.793583] usb 2-1.1: New USB device found, idVendor=15d9, idProduct=0a4f
[  271.793589] usb 2-1.1: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[  271.793592] usb 2-1.1: Product:  USB OPTICAL MOUSE[/B]

I also tried using *lsmod* with and without usb mouse plugging in, I found out the my usb is appeared as,     

**Bus 002 Device 007: ID 15d9:0a4f Trust International B.V**. 
 

By using command *usb-devices > usb* , I found out that my usb mouse is listed as below

[B]T:  Bus=02 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#=  7 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=15d9 ProdID=0a4f Rev=01.00
S:  Product= USB OPTICAL MOUSE
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=(none)[/B]


But my mouse is still not working and I have no idea how to deal with this problem. Please anyone out there, who know the way how to, let me know!!!

Gratitude in Advance,
Chit

---

