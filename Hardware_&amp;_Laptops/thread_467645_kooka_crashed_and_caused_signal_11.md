---
title: "kooka crashed and caused signal 11"
date: 2007-06-07
forum: Hardware &amp; Laptops
---

### Post by pascalg on 2007-06-07
Hi,
I am new to Ubuntu (had a debian based system before) and everything is running just fine except I can not use my scanner.
When starting Kooka it imedeatly crashes and tells me it causes signal 11.
Posted the backtrace below.
Can anybody help me with that.
thanks



(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1235580704 (LWP 6993)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#6  0xb6015bf5 in ?? () from /usr/lib/libmfp.so
#7  0xb601b880 in ?? () from /usr/lib/libmfp.so
#8  0xb601b880 in ?? () from /usr/lib/libmfp.so
#9  0xbf995438 in ?? ()
#10 0xb6017842 in m_parport_ECP_supported () from /usr/lib/libmfp.so
Backtrace stopped: frame did not save the PC

---

### Post by yabbadabbadont on 2007-06-07
Does the same thing happen if you try it with xsane?

Also, from the error trace, it looks like you have a parallel port scanner.  Is that correct?  Please list details of your hardware and which version of Ubuntu/Kubuntu/Xubuntu ... that you are using.

---

### Post by pascalg on 2007-06-08
Yes, it also dies on startup.
My scanner is a Canon N6560 scanner and connected via USB. Never had a problem with it before.
Version of Ubuntu is 7.04 with all updates applied.
Tried to reinstall kooka already. Posted a report on the kooka site already about the problem. Lots of posts about the problem under various distros but no fix.
Hope somebody can help me here.

---

