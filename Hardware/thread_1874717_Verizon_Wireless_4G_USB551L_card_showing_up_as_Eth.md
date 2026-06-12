---
title: "Verizon Wireless 4G USB551L card showing up as Ethernet connection."
date: 2011-11-03
forum: Hardware
---

### Post by apastuszak on 2011-11-03
I have a Verizon Wireless USB551L 4G Wireless card I am trying to get working in Kubuntu 11.10.  The device is not picked up as a modem but instead comes up as an ethernet connection, specifically eth1.

I'm not sure how to fix this issue.

Here is the dmesg output:

```
[ 9769.233329] usb 1-1.2: new high speed USB device number 5 using ehci_hcd
[ 9769.326988] usb 1-1.2: config 1 has an invalid interface number: 6 but max is 5
[ 9769.326993] usb 1-1.2: config 1 has an invalid interface number: 7 but max is 5
[ 9769.326997] usb 1-1.2: config 1 has an invalid interface number: 7 but max is 5
[ 9769.327001] usb 1-1.2: config 1 has no interface number 3
[ 9769.327003] usb 1-1.2: config 1 has no interface number 5
[ 9769.332322] cdc_ether 1-1.2:1.6: eth1: register 'cdc_ether' at usb-0000:00:1a.0-1.2, CDC Ethernet Device, 00:a0:c6:00:00:00
```

usb-devices shows the following:

```
T:  Bus=01 Lev=02 Prnt=02 Port=01 Cnt=01 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1410 ProdID=b001 Rev=00.15
S:  Manufacturer=Novatel Wireless, Inc.
S:  Product=Novatel Wireless 4G
S:  SerialNumber=990000462055731
C:  #Ifs= 6 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 4 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 6 Alt= 0 #EPs= 1 Cls=02(commc) Sub=06 Prot=00 Driver=cdc_ether
I:  If#= 7 Alt= 1 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_ether
```

I am hoping someone can figure out what's going on here, so I can use my 4G modem!

---

