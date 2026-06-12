---
title: "IDE/ATAPI Pcmcia controller not recognized"
date: 2009-04-07
forum: Hardware
---

### Post by ponchojuan on 2009-04-07
I've installed Ubuntu 8.10 on a Thinkpad 240 and am having trouble getting the CNF Cardport PCMCIA 24X CDROM drive to work.  The installation is stable and works fine, including the PCMCIA RA61 based WIFI card. So, it appear the general pcmcia socket drivers and yenta socket implementation are working fine, but the pcmcia ide/atapi controller does not load.  This used to be handled by the ide-cs driver, but I'm uncrear how this is supported with the new pcmciautils implementation.

The card insert/removal is detected and registered as pcmcia0.0 but no other statement is made in DMESG.  It appears no probing is initiated and the device load started.  After insertion the device config reports the following:

{config)

john@new-host-john:~$ cat /sys/bus/pcmcia/devices/*/*
cat: /sys/bus/pcmcia/devices/0.0/allow_func_id_match: Permission denied
cat: /sys/bus/pcmcia/devices/0.0/card_id: No such device
cat: /sys/bus/pcmcia/devices/0.0/func_id: No such device
0x00
cat: /sys/bus/pcmcia/devices/0.0/manf_id: No such device
pcmcia:m0000c0000f00fn00pfn00pa46D7DB81pb66536591pcE96CA5CCpd00000000
on
cat: /sys/bus/pcmcia/devices/0.0/power: Is a directory
CNF   
CD-ROM
I2
cat: /sys/bus/pcmcia/devices/0.0/prod_id4: No such device
cat: /sys/bus/pcmcia/devices/0.0/subsystem: Is a directory
SOCKET_NO=0
DEVICE_NO=00
MODALIAS=pcmcia:m0000c0000f00fn00pfn00pa46D7DB81pb66536591pcE96CA5CCpd00000000


Any thoughts on getting the CDROM recognized?

Poncho

---

### Post by ponchojuan on 2009-04-13
Well, still no luck.  Here is what gets populated in the /device dir for the pcmcia0.0.

john@new-host-john:~$ cat /sys/bus/pcmcia/devices/*/*
cat: /sys/bus/pcmcia/devices/0.0/allow_func_id_match: Permission denied
cat: /sys/bus/pcmcia/devices/0.0/card_id: No such device
cat: /sys/bus/pcmcia/devices/0.0/func_id: No such device
0x00
cat: /sys/bus/pcmcia/devices/0.0/manf_id: No such device
pcmcia:m0000c0000f00fn00pfn00pa46D7DB81pb66536591pcE96CA5CCpd00000000
ocat n
cat: /sys/bus/pcmcia/devices/0.0/power: Is a directory
CNF   
CD-ROM
I2
cat: /sys/bus/pcmcia/devices/0.0/prod_id4: No such device
cat: /sys/bus/pcmcia/devices/0.0/subsystem: Is a directory
SOCKET_NO=0
DEVICE_NO=00
MODALIAS=pcmcia:m0000c0000f00fn00pfn00pa46D7DB81pb66536591pcE96CA5CCpd00000000


Also, here is the detailed lspcmcia run:

john@new-host-john:~$ lspcmcia -vvv
Socket 0 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:00:0a.0)
	Configuration:	state: on	ready: unknown
			Voltage: 5.0V Vcc: 5.0V Vpp: 5.0V
--none--
--none--
Socket 0 Device 0:	[-- no driver --]	(bus ID: 0.0)
	Configuration:	state: on
	Product Name:   CNF    CD-ROM I2 
	Identification:	prod_id(1): "CNF   " (0x46d7db81)
			prod_id(2): "CD-ROM" (0x66536591)
			prod_id(3): "I2" (0xe96ca5cc)
			prod_id(4): --- (---)
john@new-host-john:~$ 

Looks like the driver is supposed to be pata_pcmcia best I can figure, and its not picking up my device (the module is loaded). How to set this up?  I understand there is a resource file ( Config.opts) but seems like this needs to be strapped in a vendor DB for the driver.  Any help is appreciated.

Poncho

---

