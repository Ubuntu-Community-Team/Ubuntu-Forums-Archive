---
title: "New Koala install doesn't see my Epson printer."
date: 2009-10-15
forum: Hardware
---

### Post by chris_andrew on 2009-10-15
Hi, all.

I've just done a fresh install of xubuntu 9.10.  It all went well (phew!).  Unfortunately, I can't see how to detect my printer.

When I do:
```

dmesg | grep -i epson
```(my printer manufacturer)

I get:

```
[    6.359862] scsi 6:0:0:0: Direct-Access     EPSON    Stylus Storage   1.00 PQ: 0 ANSI: 2
```

which suggests the printer has been detected on boot.

The printer was fine under Jaunty (9.04), can anyone help me set this up?

Cheers,

Chris.

---

### Post by chris_andrew on 2009-10-15
Scratch that.  Just got 300+ updates and magically my printer has just printed a test page.  I guess CUPS wasn't happy initially.

Cheers,

Chris.

---

