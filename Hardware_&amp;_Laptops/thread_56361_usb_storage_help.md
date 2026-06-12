---
title: "usb storage help"
date: 2005-08-12
forum: Hardware &amp; Laptops
---

### Post by aa33 on 2005-08-12
Hello. I was wondering if anyone could help.
I bought a memory stick pro duo magic gate 256Mb. Unfortunately it won't mount.
Is there anything i can do from the command line to coax it into mounting, if only to be able to format it properly etc.
Still relatively new to linux...
My /proc/bus/usb file relevent section reads 

T:  Bus=01 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=3538 ProdID=0015 Rev= 0.12
S:  Manufacturer=GENERIC
S:  Product=USB Mass Storage Device
S:  SerialNumber=ABCD1234567B
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=83(I) Atr=03(Int.) MxPS=   8 Ivl=10ms

when its inserted.

And less /proc/scsi/usb-storage/1 shows

  Host scsi1: usb-storage
       Vendor: GENERIC
      Product: USB Mass Storage Device
Serial Number: ABCD1234567B
     Protocol: Transparent SCSI
    Transport: Bulk
       Quirks:
also when inserted.
By the way other usb drives work fine. Its just this one (although its important for me coz it fits my digital camera)
Many thanks if anyone can help.
j

---

### Post by jasmuz on 2005-08-12
Open a terminal, type tail -f /var/log/messages and plug in your usb stick, read what it says...there must be SCSI emulation for it, if so..then just mount it to the place you want

sudo mount /dev/sda1 /whatevermountpoint

---

### Post by aa33 on 2005-08-22
Sorry for this late response. Thanks very much your help.
Much appreciated.

---

