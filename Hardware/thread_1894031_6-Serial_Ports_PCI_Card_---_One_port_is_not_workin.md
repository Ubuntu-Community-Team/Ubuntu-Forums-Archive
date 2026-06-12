---
title: "6-Serial Ports PCI Card --- One port is not working"
date: 2011-12-11
forum: Hardware
---

### Post by huntkey on 2011-12-11
Hi experts,

I recently bought this card on Ebay to give me 6 serial ports for my Cisco routers and switches for my home lab. 5 of them work fine except 1... I think that it is broken port but I still want to get confirmation here. I'm really not expert of Linux anyway. The serial console simulator software I use is minicom.

The symptom is that there is no response. When connected the minicom shows that it is "Offline". The same console cable and device works on another serial port so the device and the cable should be good.

```
dzhao@Ubuntu:~$ setserial -g /dev/ttyS* | grep -v unknown
/dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 4
/dev/ttyS4, UART: 16650V2, Port: 0xe080, IRQ: 16
/dev/ttyS5, UART: 16650V2, Port: 0xe400, IRQ: 17
/dev/ttyS6, UART: 16550A, Port: 0xec00, IRQ: 18
/dev/ttyS7, UART: 16550A, Port: 0xe880, IRQ: 18
/dev/ttyS8, UART: 16550A, Port: 0xe800, IRQ: 18
/dev/ttyS9, UART: 16550A, Port: 0xe480, IRQ: 18
```ttyS8 is the one which doesn't work. The serial configuration is:

```
+-----------------------------------------------------------------------+
| A -    Serial Device      : /dev/ttyS8                                |
| B - Lockfile Location     : /var/lock                                 |
| C -   Callin Program      :                                           |
| D -  Callout Program      :                                           |
| E -    Bps/Par/Bits       : 9600 8N1                                  |
| F - Hardware Flow Control : No                                        |
| G - Software Flow Control : No                                        |
|                                                                       |
|    Change which setting?                                              |
+-----------------------------------------------------------------------+
```All other serial ports have the same config. Is there anything else other than hardware problem which could cause this?

Thanks!

---

