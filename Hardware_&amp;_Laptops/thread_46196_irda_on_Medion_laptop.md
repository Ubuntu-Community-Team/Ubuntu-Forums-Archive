---
title: "irda on Medion laptop"
date: 2005-07-03
forum: Hardware &amp; Laptops
---

### Post by mathiasv on 2005-07-03
Hi,

I have for some time now been trying to make my Medion MD6081 communicate with my SonyEricsson K500i, but it still doesn't work. I do see my phone in irdadump:
```
20:35:44.979897 xid:cmd 11f583d2 > ffffffff S=6 s=5 (14)
20:35:45.069885 xid:cmd 11f583d2 > ffffffff S=6 s=* haddock hint=0400 [ Computer ] (23)
20:35:45.068881 xid:rsp 11f583d2 < 000049dc S=6 s=5 K500 series hint=9124 [ PnP Modem IrCOMM IrOBEX ] (28)
20:35:47.529519 xid:cmd 11f583d2 > ffffffff S=6 s=0 (14)

```
But when I try to add the module nsc-ircc (which has been used on a Medion in [http://tuxmobil.org/ir_misc.html):](http://tuxmobil.org/ir_misc.html):)
```
modprobe nsc-ircc dongle_id=0x09
FATAL: Error inserting nsc_ircc (/lib/modules/2.6.10-5-386/kernel/drivers/net/irda/nsc-ircc.ko): No such device

```

irdaping with the saddr found in /proc/net/irda/discovery gives no answer.

Can someone give a hint to what is wrong? Thanks.
Mathias

---

