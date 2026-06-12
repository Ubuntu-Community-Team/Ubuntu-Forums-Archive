---
title: "New display flickering now and then"
date: 2020-10-01
forum: Hardware
---

### Post by satimis on 2020-10-01
Hi all,

Just purchased a Dell 32" 4K U3219Q display and found it flickering to dark screen a while now and then.

Today I brought the new display to the seller.  They tested it there and there was no problem discovered.  The seller told me that the problem flickering to dark screen a while now and then may be  caused on account of the graphic card.  However there is no graphic card on my computer.  The graphic is controlled by AMD cpu.

Configuration of my desktop PC
$ lspci -nnk | grep VGA -A1```

08:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Picasso [1002:15d8] (rev c8)
Subsystem: ASUSTeK Computer Inc. Device [1043:876b]

```

Hardware Info:```

CPU:
AMD Ryzen 5 3400G with Radeon Vega Graphics
1 physical process; 4 core; 8 threads

RAM:
30791648 KiB

Motherboard:
System Version/PRIME X570-P (ASUSTek Computer inc)

Graphics:
3840x2160
(Unknown)
The X.Org Foundation

Storage:
ATA HGST HUS&26T$TAL
ASUS DRAW-24D5MT
Audio-Intel-HD-Audio Generic
```

Please advise.  Thanks

Regards

---

### Post by Autodave on 2020-10-01
Just my thoughts: you are asking too much from that onboard graphics adapter.  Possibly overheating the CPU causing it to throttle back and cause the seem like it is flickering?

---

### Post by satimis on 2020-10-02
> **Autodave said:**
> Just my thoughts: you are asking too much from that onboard graphics adapter.  Possibly overheating the CPU causing it to throttle back and cause the seem like it is flickering?
> **Autodave said:**
> Just my thoughts: you are asking too much from that onboard graphics adapter.  Possibly overheating the CPU causing it to throttle back and cause the seem like it is flickering?
It starts flickering after turning on the PC about 10-15 mins

I have made following tests;
1) Reading documents - almost no flickering
2) Browse 4K video online - no flickering
3) Browse non 4K video online - flickering occasionally
4) Browse non 4K video online and select Use=Movie on the Dell 32" 4K display - almost no flickering

Regards

---

