---
title: "hard disk corrupted"
date: 2018-08-16
forum: Hardware
---

### Post by terrorinjeoor on 2018-08-16
hello i,m new to UBUNTU....  i bought yesterday a laptop from a friend (hp compaq nc6120)  running linux ubuntu but i think my hard disk is damaged because it keeps saying ata1,00  exception emask 0x0 SAct 0x0 SErr 0x0 action 0xo ata1,00 BMDMA stat 0x65 ata1,00 failed command: READ DMA  ata1,00 cmd c0/00: 00: status {DRDY ERR}  error: {umc} end_request: 1/0 error dev sda sector 15553048 (i skipped some things because it,s hard to write)  greetings tijo

---

### Post by TheFu on 2018-08-16
Check
* bad cable
* bad disk
* bad controller port (SATA?)
* bad controller

---

### Post by Yellow Pasque on 2018-08-16
If the system is still usable, get the SMART data:
```
sudo smartctl -a /dev/sda 
```

> **TheFu said:**
> Check * bad cable
It's a laptop.

> * bad disk
Yes, that's what the OP is asking about. Suggestions on checking for a bad disk would be helpful.

> * bad controller port (SATA?)
* bad controller
Do you have suggestions on checking these without a known good disk?

---

### Post by Yellow Pasque on 2018-08-16
If the OS is unusable, there is also a hard disk self-test in the BIOS (under the Tools menu).

---

### Post by TheFu on 2018-08-16
As always, simplify and test until the problem is isolated.

Laptops have disk cables too. They go bad, but they get loose over time too. Try reseating first.

Laptops have disk controllers. They go bad. I've never had a laptop controller fail completely, but I have seen desktop motherboard  controllers fail.

The easiest way to test is often to use different hardware for each part. 

To see if it is is the disk, try a different disk. If that doesn't solve it, then it most likely isn't the original disk with the problem.  Or take the original disk and use it in a different computer with different connections and cables and controller.  Any disk issues there?

Checking smart data is useful, but 22% of disks at Backblaze fail without any data showing in the SMART information.  CRC errors in SMART are usually cable problems.

Move onto testing the cable and port and disk controller.

It is hard when a friend sells equipment that fails almost immediately, for both sides of the transaction.  Here's hoping it is the HDD, since that is the easiest/cheapest to replace.

Simplify and test.

---

