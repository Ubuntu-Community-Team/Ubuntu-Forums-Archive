---
title: "IRDA ACER Ferrari 5000 not working?"
date: 2008-12-27
forum: Hardware
---

### Post by xchip on 2008-12-27
I cant access my pocket pc using ubuntu but I can do it on windows, I used irdadump and ircp-tray but nothing worked.

I couldnt find any /dev/ircomm or /dev/irda or any /etc/irda os anythng similar, the kernel does seem to detect it


raul@xchip-ferrari:~$ lsmod | grep irda
irda                  199612  1 nsc_ircc
crc_ccitt              10112  1 irda

raul@xchip-ferrari:~$ dmesg | grep irda
[   14.934806] irda_init()

any help?
Thanks!

---

