---
title: "Uspeed USB 3.0 PCI-E Card"
date: 2012-12-28
forum: Hardware
---

### Post by mastermindg on 2012-12-28
I'm running KDE on 12.04 under kernel 3.2.0-35-generic. I was able to install another USB 3.0 PCI-E card (ioGeaar GIC320U) but I am unable to get this USpeed (WLK-898U3-4 V1.0) working correctly under 12.04.

Here's some read-outs:

The error I'm getting in dmesg is:

```
[   32.456029] hub 9-0:1.0: unable to enumerate USB device on port 4
```

LSPCI

```
02:00.0 USB controller: VIA Technologies, Inc. Device 3432 (rev 03)
```

LSUSB

```
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
```

USB-DEVICES

```
T:  Bus=09 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 4
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev=03.02
S:  Manufacturer=Linux 3.2.0-35-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:02:00.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
```

I'm connecting a powered WD MyBook. Again, this works on a different USB 3.0 card, just not this one. I'm able to plug the MyBook into a USB 2.0 port and it works fine.

---

### Post by mastermindg on 2012-12-28
I upgraded my kernel to 3.7.1 and included as much USB compatibilities as I could make sense of. I also tried:
```

modprobe xhci_hcd
```

Still not working. :sad:

---

