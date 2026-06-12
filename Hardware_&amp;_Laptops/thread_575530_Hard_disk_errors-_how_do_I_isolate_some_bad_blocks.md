---
title: "Hard disk errors- how do I isolate some bad blocks"
date: 2007-10-14
forum: Hardware &amp; Laptops
---

### Post by philinux on 2007-10-14
Got some bad blocks but they must be in part of the disk thats not used yet.

Got system on hda1 and home on hda3

smartctl give passed but there are errors in var/log messages

sample

```
high=6, low=11815319, sector=112478565
Oct 14 11:15:00 philcb-desktop kernel: [  419.636000] ide: failed opcode was: unknown
Oct 14 11:15:00 philcb-desktop kernel: [  419.636000] end_request: I/O error, dev hda, sector 112478565
Oct 14 11:15:00 philcb-desktop kernel: [  423.448000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Oct 14 11:15:00 philcb-desktop kernel: [  423.448000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=112478615, high=6, low=11815319, sector=112478573
Oct 14 11:15:00 philcb-desktop kernel: [  423.448000] ide: failed opcode was: unknown
Oct 14 11:15:00 philcb-desktop kernel: [  423.448000] end_request: I/O error, dev hda, sector 112478573
Oct 14 11:15:00 philcb-desktop kernel: [  427.272000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Oct 14 11:15:00 philcb-desktop kernel: [  427.272000] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=112478615,
```

Is there any way to fix this temporarily.

---

### Post by Linicks on 2007-10-14
You don't say what system you have, but sometimes these errors are from HD cables - reseat it, or change it.  Sometimes I have seen these errors if a HD cable wraps around/or near the PSU cables in a case.

If a laptop, try removing the drive and relocating it to ensure a good connection (obviously with the laptop OFF).

If you are convinced you have disk error:

[http://linux.die.net/man/8/badblocks](http://linux.die.net/man/8/badblocks)

Nick

EDIT:  I just found this - doesn't look promising :-(

[http://lists.debian.org/debian-laptop/2004/12/msg00134.html](http://lists.debian.org/debian-laptop/2004/12/msg00134.html)

---

### Post by philinux on 2007-10-14
I'm running feisty 7.04 on ext3.

These errors only pop up if I run fsck. I get no errors during normal operation.

I've got fsck check disabled but run it manually.

The errors from fsck are - error reading block 8684026 etc result in short read.

I get ignore error so I say Yes force rewrite Yes. Then the system boots up.

I ran badblocks and it found errors but smartctl health check says passed.

---

