---
title: "Pocket PC (Acer N50)"
date: 2005-07-02
forum: Hardware &amp; Laptops
---

### Post by tristure on 2005-07-02
Hi,

I was offered a pocket PC yesterday, it's a Acer N50.

It's my first PDA, do I'm quite unfamiliar with all this, but still I'd like to be able to sync it with ubuntu. Kubuntu actually...

Right now the problem is that Ubuntu detects the new USB device :

usb 1-1: new full speed USB device using uhci_hcd and address 3


But doesn't do anything with it.

Here's the output of cat /proc/bus/usb/devices:
T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  6 Spd=12  MxCh= 0
D:  Ver= 1.01 Cls=ff(vend.) Sub=ff Prot=ff MxPS=16 #Cfgs=  1
P:  Vendor=045e ProdID=00ce Rev= 0.00
S:  Manufacturer=Acer.
S:  Product=PocketPC
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  2mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms


I tried adding : 
BUS="usb", SYSFS{product}="PocketPC*", KERNEL="ttyUSB*", NAME{ignore_remove}="pilot", MODE="666"

to /etc/udev/rules.d/10-custom.rules, according to a howto on the wiki.

But it didn't change a thing.

Any ideas of what I could try next?

Thanks!

---

### Post by tristure on 2005-07-02
I corrected a typo in my udev rule ("PocketPC*" -> "PocketPC")

Now the system tries to do something when I plug the PDA, but doesn't succeed.

Here's what I get on dmesg:

usb 1-1: new full speed USB device using uhci_hcd and address 10
usb 1-1: device descriptor read/64, error -71

Any ideas to investigate to go further? Thanks a lot.

---

### Post by tristure on 2005-07-03
Right now the problem is that the system does not create any node in /dev, whereas kpilot or evolution are expecting something as /dev/pilot.

I tried loading the visor module manually but it didn't change anything.

Actually I don't know if this device requires the visor module or another one...

Any help really appreciated.

---

### Post by tristure on 2005-08-18
I found some useful information on the synce site.

Actually, now I made out how to have the device recognized.

First, the Acer n50, as the n30, (and many PocketPc's, it seems), needs the ipaq module.

Now even with the ipaq module loaded, the system wouldn't associate my device to the module.

So i made : cat /proc/bus/usb/devices (with the PDA plugged in), and saw the following information :

> T:  Bus=02 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  6 Spd=12  MxCh= 0
D:  Ver= 1.01 Cls=ff(vend.) Sub=ff Prot=ff MxPS=16 #Cfgs=  1
P:  Vendor=045e ProdID=00ce Rev= 0.00
S:  Manufacturer=Acer.
S:  Product=PocketPC
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  2mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms 

The vendor and ProdID are necessary, because you have to create a new file in /etc/modprobe.d. I don't think the name matters, mine is named synce and contains :
> options ipaq vendor=0x045e product=0x00ce 

Now the system sees my PDA and associates it with ipaq module, at ttyUSB0.

To make a connection, you have to follow the howto on the synce website, it is fairly easy.

So now I can connect my PDA, it has a driver, the connection is established via sync and raki... But I can't do anything useful.
rapip enables me to browse the device's filesystem, but now I woudl like to sync my adress book in kontact, and can't figure out how to do...
Any hints?

THanks for your help.

---

