---
title: "Asus Xonar DS"
date: 2012-03-20
forum: Hardware
---

### Post by LinuxBill on 2012-03-20
Trying to get sound working on my desktop install. I cant get anything out my headphones from my Xonar DS. 

lspci -v | grep -A7 -i "audio" shows the card there. 

```
08:00.0 Multimedia audio controller: C-Media Electronics Inc CMI8788 [Oxygen HD Audio]
        Subsystem: ASUSTeK Computer Inc. Virtuoso 66 (Xonar DS)
        Flags: bus master, medium devsel, latency 32, IRQ 16
        I/O ports at ce00 [size=256]
        Capabilities: <access denied>
        Kernel driver in use: AV200
        Kernel modules: snd-virtuoso
```Any advice? 

Thanks
William

---

### Post by Yellow Pasque on 2012-03-20
What version of Ubuntu are you running?

---

### Post by LinuxBill on 2012-03-21
Latest Kbuntu version.

---

