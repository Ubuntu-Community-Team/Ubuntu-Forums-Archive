---
title: "check Hardware compatibility via LIVE CD"
date: 2012-11-14
forum: Hardware
---

### Post by kashif12 on 2012-11-14
Hi

Can i use LIVE CD to verify that ubuntu has all drivers present for a certain desktop PC?


Before i purchase this expensive PC i want to ensure ubuntu has all drivers for it.

Specs are :

Processor Intel Core i7 3770
Motherboard Intel  DH77KC 
2 HD Western Digital 500 GB
4 LAN cards.

I will use this server to run virtual machines, run solaris etc.
as i think Solaris will not install on this machine directly because of drivers issues
I also plan to run ubuntu server version on this system :guitar:

---

### Post by carl4926 on 2012-11-14
> Can i use LIVE CD to verify that ubuntu has all drivers present for a certain desktop PC?
If you have access to it, yes. It will certainly help.

If you open a terminal and do

```
lspci -nnk
```it will list devices and kernel modules loaded

---

