---
title: "Laptop frozen - hard drive or sys board failing?"
date: 2011-10-09
forum: Hardware
---

### Post by dreampen51388 on 2011-10-09
My laptop will freeze from time to time. I saw this from syslog
Which hardware was failing? Please advise. Thanks !

Oct  9 09:38:00 laptop-1 kernel: [ 9489.274862] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Oct  9 09:38:00 laptop-1 kernel: [ 9489.274875] ata3.00: BMDMA stat 0x4
Oct  9 09:38:00 laptop-1 kernel: [ 9489.274886] ata3.00: failed command: READ DMA
Oct  9 09:38:00 laptop-1 kernel: [ 9489.274906] ata3.00: cmd c8/00:18:a8:70:c9/00:00:00:00:00/e5 tag 0 dma 12288 in
Oct  9 09:38:00 laptop-1 kernel: [ 9489.274910]          res 51/40:12:ae:70:c9/40:00:05:00:00/e5 Emask 0x9 (media error)
Oct  9 09:38:00 laptop-1 kernel: [ 9489.274919] ata3.00: status: { DRDY ERR }
Oct  9 09:38:00 laptop-1 kernel: [ 9489.274925] ata3.00: error: { UNC }
Oct  9 09:38:00 laptop-1 kernel: [ 9489.296282] ata3.00: configured for UDMA/100
Oct  9 09:38:00 laptop-1 kernel: [ 9489.296316] ata3: EH complete
Oct  9 09:38:04 laptop-1 kernel: [ 9493.874740] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0

---

