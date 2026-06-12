---
title: "kubuntu 7.10 and 8.04 + Cell phone in usb mode"
date: 2008-01-31
forum: Hardware &amp; Laptops
---

### Post by cansei on 2008-01-31
Hi, I'm a Kubuntu user and I have a problem with my cell phone  (Motorola V360 - USB Storage mode)

On XP and Kubuntu 7.04 it works fine but when I upgraded to 7.10 it didnt worked anymore, I tried to upgrade again to hardy but still not working

On 7.04 when I plug it I could easily access my files through a desktop icon or /media but on 7.10 and 8.04 nothing happens


I found ohter people with similar problems but nobody with a concrete solution

My lsusb:

> Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 22b8:4810 Motorola PCS Triplet GSM Phone (storage)
Bus 001 Device 001: ID 0000:0000

dmesg showed a lot of things like this:

> [  259.617269] Buffer I/O error on device sdc, logical block 123864
[  259.771996] sd 2:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  259.772013] sd 2:0:0:0: [sdc] Sense Key : Medium Error [current]
[  259.772019] sd 2:0:0:0: [sdc] Add. Sense: No additional sense information
[  259.772025] end_request: I/O error, dev sdc, sector 990912

Thanks and sorry for my english

---

