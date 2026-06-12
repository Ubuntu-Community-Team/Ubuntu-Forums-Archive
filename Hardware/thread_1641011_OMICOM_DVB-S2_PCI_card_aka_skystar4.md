---
title: "OMICOM DVB-S2 PCI card aka skystar4"
date: 2010-12-08
forum: Hardware
---

### Post by faris-uppercut on 2010-12-08
Recently installed ubuntu 10.10, has improved alot since I lost used ubuntu. Onto topic, the only piece of hardware I cant get working is my tv card its OMICOM DVB-S2 PCI card  think it is sometimes refereed to as skystar 4, on the box it says compatible with linux but the CD only has windows drivers, how can I install drivers for this card?

when I try and use it it fails so It must not be installed right.
```
 scan -x0 /usr/share/dvb/dvb-s/Astra-28.2E | tee channels.conf
scanning /usr/share/dvb/dvb-s/Astra-28.2E
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2273: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 2 No such file or directory

```Also when i do  lspci -vnn I get 
00:0a.0 Multimedia controller [0480]: Philips Semiconductors SAA7146 [1131:7146] (rev 01)
    Subsystem: IWASAKI Information Systems Co Ltd Device [14c4:1020]
    Flags: bus master, medium devsel, latency 64, IRQ 11
    Memory at f9fffc00 (32-bit, non-prefetchable) [size=512]
This part is refering to my tv card

---

