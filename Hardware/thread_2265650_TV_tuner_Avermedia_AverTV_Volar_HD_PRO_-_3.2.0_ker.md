---
title: "TV tuner Avermedia AverTV Volar HD PRO - 3.2.0 kernel"
date: 2015-02-16
forum: Hardware
---

### Post by g117 on 2015-02-16
Hi,

I'm trying to get my TV card Avermedia AverTV Volar HD PRO working on ElementaryOS (based on Ubuntu, kernel version 3.2.0-76-generic). I've tried some tutorials I've found, but nothing works, actually. The problem is that it looks like the Tv card wasn't detected - there is no /dev/dvb file. But when I run ```
lsusb
``` command, I get: ```
Bus 002 Device 005: ID 07ca:1835 AVerMedia Technologies, Inc.
``` And there is even no an error log - I ran ```
dmesg | grep dvb
``` and I've got nothing. 

Can anybody suggest me what to try or what to look for? In the past, I was able to get this card running on the newer kernel, but I switched to ElementaryOS, whis uses this older kernel. 

Thanks.

---

