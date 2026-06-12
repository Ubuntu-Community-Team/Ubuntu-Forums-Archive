---
title: "I can't use my cdrom after upgrade to 8.10"
date: 2008-12-06
forum: Hardware
---

### Post by sensez on 2008-12-06
My cdrom is (lshw):

 [COLOR="Blue"]             description: DVD reader
                product: DVD-ROM SD-C2502
                vendor: TOSHIBA
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1711
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=open[/COLOR]

I can't use my cdrom after upgrade to 8.10 with kernel 2.6.27. It's warning 

[COLOR="Blue"]Buffer I/O error on device sr0, logical block 22 ... 
Buffer I/O error on device sr0, logical block 22 ...[/COLOR]

But in 8.04.1 with the same cd, it's ok. And if I switch kernel to 2.6.24 in 8.10, it will be ok too. Can I fix this with the new kernel? Thanks!

---

