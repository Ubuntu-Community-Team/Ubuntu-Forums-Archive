---
title: "Hard Drive Errors After New Install"
date: 2010-02-05
forum: Hardware
---

### Post by LighthouseJ on 2010-02-05
I just installed Ubuntu 9.10 fresh ontop of an older Ubuntu.

Now all of the sudden, I get these messages:

> 
[ 6511.988036] ata5: lost interrupt (Status 0x51)
[ 6511.988068] ata5.00: limiting speed to PIO4
[ 6511.988073] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 6511.989091] ata5.00: cmd ca/00:00:bf:31:15/00:00:00:00:00/e0 tag 0 dma 131072 out
[ 6511.989094]          res 40/00:01:3e:ee:0e/00:00:00:00:00/e0 Emask 0x4 (timeout)
[ 6511.991735] ata5.00: status: { DRDY }
[ 6511.992732] ata5: soft resetting link
[ 6512.172401] ata5.00: configured for PIO4
[ 6512.180420] ata5.01: configured for PIO4
[ 6512.180432] ata5: EH complete


ata5 is the IDE controller to two drives that are in a software RAID.  I also get the same sort of thing on my main SATA hard drive with the OS too.

Beyond the obvious "your hard drives are going bad", is there something I can do about this?  The machine never had a single problem before up to the day I reinstalled Ubuntu.

---

### Post by kidders on 2010-02-06
Hi there,

> **LighthouseJ said:**
> Beyond the obvious "your hard drives are going bad", is there something I can do about this?There's nothing there to suggest a problem with your hard disk, although if you want to be *sure*, there's no harm in checking out it's SMART status.

The problem is more likely something to do with the way libata is interacting with your ATA bus, but I'm afraid I don't know *nearly* enough to figure it out for you on the basis of a short log extract. Some possibilities include ...[LIST]
[*]A kernel/libata bug
[*]A bug in your ATA controller
[*]Your usage pattern.
[/LIST]

For instance, the fact that you're using software RAID makes me suspicious. You could simply be shoving too much data down your I/O bus. Are you able to trigger the problem by performing lots of I/O? Does it still occur when the RAID array is not mounted? It's also conceivable that the problem might tend to crop up at very regular intervals ... ie it might coincide with a buffer being flushed. That ought to cover the usage patterns angle.

You could rule out kernel-level issues by switching to a different version ... either upgrading or downgrading by a few revisions might magically resolve the problem.

Beyond that, you could try searching for similar issues involving your I/O controller hardware. In your shoes, my first thought would be to stop using the RAID array for a little while though, and see if that has any effect.

---

