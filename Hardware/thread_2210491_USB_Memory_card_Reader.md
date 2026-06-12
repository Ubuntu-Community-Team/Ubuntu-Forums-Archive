---
title: "USB Memory card Reader"
date: 2014-03-11
forum: Hardware
---

### Post by vs-punn on 2014-03-11
Ubuntu Version: 13.10 (32 Bit).
I have a USB Memory Card Reader. I can use it on a Windows Platform, but not on Ubuntu.

When I attach the Card Reader, and check under terminal using lsusb, I get:
Bus 002 Device 005: ID 14cd:8125 Super Top SD MMC Reader

But the device doesnot show under media.
How can  I use the device under Ubuntu.

---

### Post by ajgreeny on 2014-03-11
I assume there is a memory card in the card reader?  If not there will be nothing to show in /media.

If that still doesn't work plug the reader in (with a card inserted) then immediately run **tail /var/log/dmesg** and post the output back here.

---

