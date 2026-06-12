---
title: "new WD3200jbrtl HD freezing system during torrent downloads"
date: 2008-10-13
forum: Hardware
---

### Post by dturner on 2008-10-13
I just put in a new hard drive and it seems like when it gets to an approximate capacity (/dev/sda1            307858420  99004276 193338972  34% /
)this happens

ata1.00: status: { DRDY ERR }
ata1.00: configured for PIO0
ata1: EH complete
ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
ata1.00: cmd c4/00:08:bf:ed:79/00:00:00:00:00/eb tag 0 pio 4096 in
res 51/01:08:c0:ed:79/00:00:00:00:00/eb Emask 0x1 (device error)


over and over again , won't let me recover have to do a hard reboot by the switch. 

It seems to mostly happen when i open up ktorrent so i assume It has something to do with high activity and not really directly related to ktorrent. If anyone has any ideas please help I appreciate it.
 
theres some bits from syslog and dmesg here [http://paste.ubuntu.com/57038/](http://paste.ubuntu.com/57038/)

Dave

---

