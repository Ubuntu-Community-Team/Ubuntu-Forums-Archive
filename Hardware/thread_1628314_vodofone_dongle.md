---
title: "vodofone dongle"
date: 2010-11-22
forum: Hardware
---

### Post by michaelmurkers on 2010-11-22
hello all I am trying to get my vodafone dongle to connect in x86 ubuntu 64 bit

here is the usb device info:

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 0uld 
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=1008 Rev=00.00
S:  Manufacturer=Vodafone (ZTE)
S:  Product=Vodafone Mobile Broadband K3570-Z
S:  SerialNumber=P680A8VDFD000000
C:  #Ifs= 5 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 4 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option

any help would be greatly appreciated

its flashing light blue however when i have tried to work it using network connections and trying to put in the atp ect it has not worked

---

### Post by michaelmurkers on 2010-11-23
please can someone help me or im going to have to install xp

---

### Post by Fafler on 2010-11-23
We can't have you running around installing XP, so i quess we need to figure this one out. The info you've posted is not the most useful. Please open a terminal and type
```
tail -f /var/log/messages
```
Now connect the dongle and post the results.

---

### Post by jimmers on 2010-11-23
Google betavine.net and look for ubuntu.tgz, download and install
This is ho I got my Dongle, the model same as yours to work.

Luck

---

