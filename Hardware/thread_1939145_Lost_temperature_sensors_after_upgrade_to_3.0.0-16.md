---
title: "Lost temperature sensors after upgrade to 3.0.0-16"
date: 2012-03-11
forum: Hardware
---

### Post by NigelRen on 2012-03-11
After the recent upgrade to 3.0.0-16 the ability to read sensors which were reporting cpu temperatures etc. has stopped working.
I've booted back into 3.0.0-15 and they seem to work OK.
The hardware I'm running is an XW9400 motherboard ( a Tyan S2915 ish board ).
Using sensors-detect seems to add in the same module ( smsc47b397 is in /etc/modules, it's been there a few days so a few reboots since then ), but now when I run sensors I get 'No sensors found!'.

---

