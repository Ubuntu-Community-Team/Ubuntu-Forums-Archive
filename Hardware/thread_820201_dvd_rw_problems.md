---
title: "dvd rw problems"
date: 2008-06-06
forum: Hardware
---

### Post by vonschutter on 2008-06-06
What does this mean in syslog?? My dvd does not work in Ubuntu, but I did install Ubuntu from said drive. 

Jun  6 01:07:17 burner kernel: [28419.087710] ata3.00: configured for PIO0
Jun  6 01:07:17 burner kernel: [28419.087728] ata3: EH complete
Jun  6 01:07:47 burner kernel: [28436.748509] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Jun  6 01:07:47 burner kernel: [28436.748520] ata3.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Jun  6 01:07:47 burner kernel: [28436.748521]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Jun  6 01:07:47 burner kernel: [28436.748523]          res 40/00:02:00:08:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Jun  6 01:07:47 burner kernel: [28436.748526] ata3.00: status: { DRDY }
Jun  6 01:07:47 burner kernel: [28436.748541] ata3: soft resetting link
Jun  6 01:07:47 burner kernel: [28436.994650] ata3.00: configured for PIO0
Jun  6 01:07:47 burner kernel: [28436.994658] ata3: EH complete

---

