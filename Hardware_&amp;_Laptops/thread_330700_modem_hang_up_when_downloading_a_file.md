---
title: "modem hang up when downloading a file"
date: 2007-01-03
forum: Hardware &amp; Laptops
---

### Post by gazmon on 2007-01-03
My AC 97 modem works great if I navigate web, but if I try to download any file, it hang up when it has downloaded about 1MB. So pppd die and I need to reconnect and, if it's possible, reconnect for another 1MB to download! Very strange for me ](*,) 
```

#lspci -v 
...
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
        Subsystem: Benq Corporation Unknown device 5005
        Flags: bus master, medium devsel, latency 0, IRQ 6
        I/O ports at e200 [size=256]
        I/O ports at e300 [size=128]
        Capabilities: <access denied>
...

```

---

