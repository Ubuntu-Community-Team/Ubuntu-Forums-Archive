---
title: "buffer IO read errors to do with sr0 in logs"
date: 2010-07-10
forum: Hardware
---

### Post by madubuntuer on 2010-07-10
minutes to boot on a Asus G70, with Duo T9500. I hope a more stable 10.4.

[24230.537875] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current]
[24230.537893] Info fld=0x0
[24230.537898] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[24230.537911] end_request: I/O error, dev sr0, sector 0
[24230.537919] __ratelimit: 29 callbacks suppressed
[24230.537925] Buffer I/O error on device sr0, logical block 0
[24230.537936] Buffer I/O error on device sr0, logical block 1
[24230.537943] Buffer I/O error on device sr0, logical block 2
[24230.537950] Buffer I/O error on device sr0, logical block 3
[24230.537956] Buffer I/O error on device sr0, logical block 4
[24230.537962] Buffer I/O error on device sr0, logical block 5
[24230.537969] Buffer I/O error on device sr0, logical block 6
[24230.537975] Buffer I/O error on device sr0, logical block 7
[24230.537981] Buffer I/O error on device sr0, logical block 8
[24230.537987] Buffer I/O error on device sr0, logical block 9
[24230.541425] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE

Why am I getting these errors? Why does it even access the dvd writer? Theres no cd/dvd in the drive and I haven't access the drive.
It seems to happen during bootup

---

