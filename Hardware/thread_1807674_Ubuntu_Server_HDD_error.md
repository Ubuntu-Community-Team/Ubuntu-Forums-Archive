---
title: "Ubuntu Server HDD error"
date: 2011-07-19
forum: Hardware
---

### Post by tech_ninja on 2011-07-19
After a clean install of Ubuntu Server edition 64-bit im getting the lines shown below. The lines are from /var/log/kern.log This was happening even before formatting the whole hard-disk(hence the format). The system usually slows down and freezes after these lines. BTW im a complete beginner in Ubuntu.

Jul 19 19:09:01 hostname kernel: [   77.391914] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Jul 19 19:09:01 hostname kernel: [   77.391984] ata3.00: BMDMA stat 0x26
Jul 19 19:09:01 hostname kernel: [   77.392019] ata3.00: failed command: READ DMA
Jul 19 19:09:01 hostname kernel: [   77.392063] ata3.00: cmd c8/00:90:70:bd:13/00:00:00:00:00/e0 tag 0 dma 73728 in
Jul 19 19:09:01 hostname kernel: [   77.392065]          res 51/84:90:70:bd:13/84:02:01:00:00/e0 Emask 0x30 (host bus error)
Jul 19 19:09:01 hostname kernel: [   77.392193] ata3.00: status: { DRDY ERR }
Jul 19 19:09:01 hostname kernel: [   77.392228] ata3.00: error: { ICRC ABRT }
Jul 19 19:09:01 hostname kernel: [   77.392275] ata3: soft resetting link
Jul 19 19:09:01 hostname kernel: [   77.610254] ata3.00: configured for UDMA/100
Jul 19 19:09:01 hostname kernel: [   77.610268] ata3: EH complete

---

### Post by tech_ninja on 2011-07-23
Please Help

---

### Post by 2F4U on 2011-07-23
It may be indeed a bad hard disk. However, in this post, there is a pointer to a bad acpi implementation and a workaround is given, which you may wish to try

[http://ubuntuforums.org/archive/index.php/t-1034762.html](http://ubuntuforums.org/archive/index.php/t-1034762.html)

---

### Post by tech_ninja on 2011-07-26
Thanks. But i actually got it work again by swapping the port it was connected to on the motherboard. It's been running for 2 days with no problems.

---

