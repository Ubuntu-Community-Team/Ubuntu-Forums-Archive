---
title: "Dvd Writer not recognized all of a sudden"
date: 2010-02-03
forum: Hardware
---

### Post by dips0502 on 2010-02-03
Okay, so here is the story...
One fine day, I realized that Brasero Disc burner was having difficulty in writing an iso file to a CD that I had just purchased. Initially I thought the CD was defective . Replaced the CD still didnt succeed. Tried K3b...still no success..All this while even though it couldn't write to the disc , it at least read it as a blank CD.

Some days later, it stopped reading as well. Now I cant even boot any of my Linux Live CDs.. This is what dmesg output is when I load a DVD into it..I havnt had a chance to see if the DVD Writer works on another Desktop system...But for now what do u guys think of the dmesg output ?

[11837.380647] sr0: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[11837.380661] sr: Sense Key : Hardware Error [current] 
[11837.380665] sr: Add. Sense: Logical unit communication time-out
[11837.532137] sr 4:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[11837.532143] sr 4:0:1:0: [sr0] Sense Key : Aborted Command [current] 
[11837.532148] sr 4:0:1:0: [sr0] Add. Sense: Beginning-of-partition/medium detected
[11837.532154] end_request: I/O error, dev sr0, sector 64
[11837.532159] Buffer I/O error on device sr0, logical block 8
[11837.534194] sr 4:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[11837.534199] sr 4:0:1:0: [sr0] Sense Key : Aborted Command [current] 
[11837.534203] sr 4:0:1:0: [sr0] Add. Sense: Beginning-of-partition/medium detected
[11837.534207] end_request: I/O error, dev sr0, sector 64
[11837.534210] Buffer I/O error on device sr0, logical block 8
[11837.547128] sr0: CDROM (ioctl) error, command: Get configuration 46 00 00 00 00 00 00 00 20 00
[11837.547141] sr: Sense Key : Hardware Error [current] 
[11837.547144] sr: Add. Sense: Logical unit communication time-out
[11837.861232] sr 4:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[11837.861239] sr 4:0:1:0: [sr0] Sense Key : Aborted Command [current] 
[11837.861244] sr 4:0:1:0: [sr0] Add. Sense: Beginning-of-partition/medium detected
[11837.861250] end_request: I/O error, dev sr0, sector 72
[11837.861255] Buffer I/O error on device sr0, logical block 9
[11837.861260] Buffer I/O error on device sr0, logical block 10
[11837.861263] Buffer I/O error on device sr0, logical block 11
[11837.861266] Buffer I/O error on device sr0, logical block 12
[11837.861269] Buffer I/O error on device sr0, logical block 13
[11837.861273] Buffer I/O error on device sr0, logical block 14
[11837.861275] Buffer I/O error on device sr0, logical block 15
[11837.861279] Buffer I/O error on device sr0, logical block 16
[11837.862987] sr 4:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[11837.862991] sr 4:0:1:0: [sr0] Sense Key : Aborted Command [current] 
[11837.862995] sr 4:0:1:0: [sr0] Add. Sense: Beginning-of-partition/medium detected
[11837.862999] end_request: I/O error, dev sr0, sector 64

---

### Post by dips0502 on 2010-02-07
Faulty IDE cable...Now the DVD drive is working...:D

---

