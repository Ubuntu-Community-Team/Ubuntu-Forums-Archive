---
title: "Sudden hard freezing"
date: 2006-09-29
forum: Hardware &amp; Laptops
---

### Post by macogw on 2006-09-29
I can find no pattern to when it happens, but my computer goes into hard freezes.  After a few times I did look at the clock so I'd know what time to check in the syslog.

Sep  7 16:42:19 localhost kernel: [17180054.844000] ide: failed opcode was: unknown
Sep  7 16:42:19 localhost kernel: [17180054.844000] hda: DMA disabled
Sep  7 16:42:49 localhost kernel: [17180084.844000] hda: ATAPI reset timed-out, status=0x90
Sep  7 16:43:24 localhost kernel: [17180114.844000] ide0: reset timed-out, status=0x80
Sep  7 16:43:24 localhost kernel: [17180119.848000] hda: status timeout: status=0x80 { Busy }
Sep  7 16:43:24 localhost kernel: [17180119.848000] ide: failed opcode was: unknown
Sep  7 16:43:24 localhost kernel: [17180119.848000] hda: drive not ready for command
Sep  7 16:43:54 localhost kernel: [17180149.848000] hda: ATAPI reset timed-out, status=0x80
Sep  7 16:44:24 localhost kernel: [17180179.848000] ide0: reset timed-out, status=0x80


Yes, it's been a while.  I've been putting up with it (it stopped after a few days and then restarted a couple days ago).  A few people suggested it was a bad hdd based on ide0, but I have an SATA hdd (that's hda).  I'm pretty sure ide0 is my cd drive (that's the only ide thing I can think of in there).  I just googled it again, and saw someone pointing out that hda does something at the same time.  So, I looked back in there and noticed those hda lines.  Googled for ATAPI, and it's a cd drive thing.  So, I'm back to not sure if my hdd or the cd drive is the source of my problems.  Does anybody know what I should do to get it to stop doing this for good?  Or do I need to replace some hardware?

---

