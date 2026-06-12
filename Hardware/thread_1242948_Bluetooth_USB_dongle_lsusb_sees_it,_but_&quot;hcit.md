---
title: "Bluetooth USB dongle: lsusb sees it, but &quot;hcitool scan&quot; says &quot;No such device&quot;"
date: 2009-08-17
forum: Hardware
---

### Post by mondalaci on 2009-08-17
Hi guys,

```
laci@whisper:~$ lsusb | grep Bluetooth
Bus 002 Device 021: ID 0a5c:2100 Broadcom Corp. Bluetooth 2.0+eDR dongle
laci@whisper:~$ hcitool scan
Device is not available: No such device
laci@whisper:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"

```
What now?

Thanks in advance!

---

### Post by billdotson on 2009-08-17
I don't know but it might have something to do with the way it is seen by the OS, that is as "device 021." However, I cannot find out what those device codes from lsusb mean anywhere so that is all I can help you with.

---

