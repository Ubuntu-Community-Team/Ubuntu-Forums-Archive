---
title: "SamsungSyncMaster 226bw with vesa drivers"
date: 2008-08-22
forum: Hardware
---

### Post by bPawn on 2008-08-22
Hi,

lets make it quick.

```
lspci -nn | grep VGA
```

and I get: 

```
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Mobilitiy Radeon HD 3450 [1002:95c5]
```

(btw I don't know why there is a spelling error...)

The  Official proprietary drivers ,from ati, corrupt my RAM, (x86_64, 8GB RAM) and the open source ones do not work either.

I have a SamsungSyncMaster 226bw 22'' wide screen monitor that should work at 1680x1050 60Hz. 

I want to use the VESA driver.

how should i configure my xorg.conf?

thanks!

---

### Post by prshah on 2008-08-22
> **bPawn said:**
> 
lets make it quick.
I want to use the VESA driver.


No more xorg.conf.

Alt+F2, ```
gksudo displayconfig-gtk
``` "Graphics Card" Tab, Choose "Vesa" for driver. OK.

---

