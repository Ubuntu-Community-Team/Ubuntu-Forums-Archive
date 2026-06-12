---
title: "dial up connection difficulties"
date: 2005-01-13
forum: Hardware &amp; Laptops
---

### Post by varla on 2005-01-13
Hi I am of course a newbie and I am waiting for my DSL to kick in... In the meantime I am trying to get my internal modem to dial up a connection and I am failing miserably. I have configured in the Network setting tool and I can't connect.
I am looking into wvdial.conf to see :

[Dialer pp0]
Init2 = ATL1
Stupid mode = 0
Init1 = ATZ

Password = mypassword
Phone = 8882228
Username = varla
Dial Command =ATDT

when I do the wvdial command I get

--> WvDial: Internet dialer version 1.54.0
--> Warning: section [Dialer Defaults] does not exist in wvdial.conf
--> Cannot open /dev/modem/: No such file or directory
--> Cannot open /dev/modem/: No such file or directory
--> Cannot open /dev/modem/: No such file or directory

I am lost!

Help anyone

Thanks.

---

