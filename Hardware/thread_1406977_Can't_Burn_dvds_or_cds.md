---
title: "Can't Burn dvds or cds"
date: 2010-02-14
forum: Hardware
---

### Post by emperium on 2010-02-14
hello, 
I'm having this problem, when I try to use Brasero it only permit to burn an ISO image.
It doesn't recognize my DVD-RW LG GSA N20T (Fujitsu Siemens V5515 laptop)
but when I do [PHP]$sudo lshw[/PHP] I get this 

```
cdrom
                description: DVD-RAM writer
                product: DVDRAM GSA-T20N
                vendor: HL-DT-ST
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: WW01
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc

```so, can anyone tell me what's is wrong?

I'm using Ubuntu Karmic Koala with Kernel 2.6.31-19

Thank you.

EmperiuM

---

