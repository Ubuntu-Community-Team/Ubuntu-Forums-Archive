---
title: "Failing Hard Drive"
date: 2009-07-09
forum: Hardware
---

### Post by SmokinJuan on 2009-07-09
My server crashes fairly regularly. Very annoying.  It's in a basement that isn't what I'd call pristine - semi-damp and spiders.  I try to keep the bugs out of it, but they're pretty quick.  The server itself is fairly old, maybe 7-8 years.  I *want* to blame the problems on the spiders since they can be cleaned out at no cost, and cleaning *seems* to make a difference, but with the age of the machine I'm guessing one of the hard drives has about had it.  Lately, upon reboot it needs a manual fsck.  I'm not exactly sure what inodes are, but it seems the numbers that fsck spits out tend to be about the same.  It's gotten to the point where I decided to check the logs.  The following is from /messages.  So, what's the prognosis? 

```
Jul  2 09:50:39 server kernel: [42995118.600000] hda: dma_timer_expiry: dma status == 0x61
Jul  2 09:50:40 server kernel: [42995128.600000] hda: DMA timeout error
Jul  2 09:50:40 server kernel: [42995128.600000] hda: dma timeout error: status=0xd0 { Busy }
Jul  2 09:50:40 server kernel: [42995128.600000] ide: failed opcode was: unknown
Jul  2 09:50:40 server kernel: [42995128.600000] hda: DMA disabled
Jul  2 09:50:40 server kernel: [42995128.600000] hdb: DMA disabled
Jul  2 09:50:40 server kernel: [42995128.700000] ide0: reset: success
Jul  2 09:50:40 server kernel: [42995148.750000] hda: dma_timer_expiry: dma status == 0x21
Jul  2 09:50:40 server kernel: [42995158.750000] hda: DMA timeout error
Jul  2 09:50:40 server kernel: [42995158.750000] hda: dma timeout error: status=0x58 { DriveReady SeekComplete DataRequest }
Jul  2 09:50:40 server kernel: [42995158.750000] ide: failed opcode was: unknown
Jul  2 09:50:40 server kernel: [42995163.760000] hda: status timeout: status=0xd0 { Busy }
Jul  2 09:50:40 server kernel: [42995163.760000] ide: failed opcode was: unknown
Jul  2 09:50:40 server kernel: [42995163.810000] ide0: reset: success
```

---

### Post by srt4play on 2009-07-09
> **SmokinJuan said:**
> So, what's the prognosis?

Looks like you diagnosed the problem pretty good with the title of your thread.

---

