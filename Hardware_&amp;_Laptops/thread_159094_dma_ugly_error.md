---
title: "dma ugly error"
date: 2006-04-12
forum: Hardware &amp; Laptops
---

### Post by IGNIZ on 2006-04-12
hi all, i have an ugly dma error at startup, it's something like this:

localhost kernel [4294977.759000] hda: dma_timer_expiry: dma status == 0x61
localhost kernel [4294987.759000] hda: DMA timeout error
localhost kernel [4294987.759000] hda: dma timeout error: status=0x58 { DriveReady SeekComplete DataRequest }
localhost kernel [4294987.759000] 
localhost kernel [4294987.759000] ide: failed opcode was: unknown
localhost kernel [4295047.888000] hdb: lost interrupt

this happen lots of times at boot, and it's the same if i try to start dma from a shell

sometimes i don't have the problem and it goes all good at boot, some other times it hangs at start for 2 minutes and then it starts without dma

what can be the problem? a kernel one, an hd one or a mobo one? 
(i suppose it's a mobo one because i've xp on another hd and now it takes a lot to boot... just the same of my ubuntu)

is my mobo going to die? or it's just a kernel problem? please help me

---

