---
title: "&quot;hw csum wrong&quot; message in dmesg, after replacing hdd"
date: 2008-09-01
forum: Hardware
---

### Post by rogeriopvl on 2008-09-01
Hi,

I've recently had to change my hdd from IDE to SATA. I cloned the old disk containing Ubuntu to the new one with dd.

When I booted from the new disk, everything apparently was alright. No problems. But when I do dmesg to see the messages, I have the following entry:

```
[131414.716200] atl1 0000:01:00.0: hw csum wrong, pkt_flag:1600, err_flag:80
[138272.843357] atl1 0000:01:00.0: hw csum wrong, pkt_flag:1600, err_flag:80
[144429.786342] atl1 0000:01:00.0: hw csum wrong, pkt_flag:1600, err_flag:80
[145740.928513] atl1 0000:01:00.0: hw csum wrong, pkt_flag:1600, err_flag:80
[145937.508653] atl1 0000:01:00.0: hw csum wrong, pkt_flag:1600, err_flag:80
[167029.961460] atl1 0000:01:00.0: hw csum wrong, pkt_flag:1600, err_flag:80
```

As I said, after about 4 days with the new disk, I haven't seen yet a real problem with the system. But those entries in dmesg annoy me, and they seem to be something like a checksum that Ubuntu makes to the hardware to verify if it has changed.

Does anyone know how to solve this? or to recalculate the sum?

Thanks in advance

---

### Post by IntuitiveNipple on 2008-09-01
Does the system have a Attansic Ethernet network adapter?

The error message you report is generated in the atl1 driver:
```

ubuntu-hardy$ egrep -rn 'hw csum' drivers/net/*
drivers/net/atl1/atl1_main.c:1174:		"hw csum wrong, pkt_flag:%x, err_flag:%x\n",

```

---

### Post by rogeriopvl on 2008-09-01
> **IntuitiveNipple said:**
> Does the system have a Attansic Ethernet network adapter?

The error message you report is generated in the atl1 driver:
```

ubuntu-hardy$ egrep -rn 'hw csum' drivers/net/*
drivers/net/atl1/atl1_main.c:1174:		"hw csum wrong, pkt_flag:%x, err_flag:%x\n",

```

Yes!

Output of lspci:
```
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)

```

So I assume that it has nothing to with the hdd change? Probably I already getting it before the change.

---

### Post by IntuitiveNipple on 2008-09-01
> **rogeriopvl said:**
> 
So I assume that it has nothing to with the hdd change? Probably I already getting it before the change.
Quite possibly. It might be worth investigating in a more leisurely manner though in case there's an issue behind it :)

---

### Post by rogeriopvl on 2008-09-01
Thanks, I'll check it out then :)

---

### Post by SigmundFreud on 2008-09-03
> **rogeriopvl said:**
> Thanks, I'll check it out then :)

I have the same network adapter and get the checksum error all the time. I haven't been able to find out what causes it and how to fix it. I'm not sure if it's a bug, too.

---

### Post by IntuitiveNipple on 2008-09-03
I suspect the root cause is that many network hardware devices are now offloading packet checksum generation into hardware. They have traditionally been calculated in software. Possibly the driver and hardware aren't quite in sync, leading to this report in some circumstances.

---

### Post by edong23 on 2010-12-09
i just wanted to chime in here.  i know the post is old.. but someone searching might want to hear this.  im not using ubuntu, im not a ubuntu user.. and i have this error on a server in my office. (older pc based server) and it has been running for 5 years with this error filling up dmesg.  never had an issue.  i agree it is likely what IntuitiveNipple thinks, or something along the lines of the kernel not being able to read some aspect of the card.   it does not hurt anything. this is a busy server and this has never affected performance.

---

