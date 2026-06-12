---
title: "fiber channel driver resetting"
date: 2011-05-16
forum: Hardware
---

### Post by ub007 on 2011-05-16
Hi,
 
I see a spew of the following in 'dmesg' on my proliant server.

Could someone shed some light on what that means?
To me it looks like fibrer channel (qlogic) driver is resettng - a possible hardware or module bug.....

> qla2xxx_trgt 0000:1e:00.0: Performing ISP error recovery - ha= ffff810c231944f8.

qla2xxx_trgt 0000:1e:00.0: ZIO mode 5 enabled; timer delay (200 us).

qla2xxx_trgt 0000:1e:00.0: LOOP UP detected (4 Gbps).

qla2xxx_trgt 0000:1e:00.1: Performing ISP error recovery - ha= ffff810c22f884f8.

qla2xxx_trgt 0000:1e:00.1: ZIO mode 5 enabled; timer delay (200 us).

qla2xxx_trgt 0000:1e:00.1: LOOP UP detected (4 Gbps). 

Thanks in advance
Dav

---

