---
title: "hdd problem"
date: 2007-09-24
forum: Hardware &amp; Laptops
---

### Post by arjanhs on 2007-09-24
After starting my ubuntu server, the following messages apear on the screen:

[   45.040404] Buffer I/O error on device hda6, logical block 28
[   46.377370] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[   46.377377] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=18073268, sector=18073246
[   46.377387] ide: failed opcode was: unknown
[   46.377392] end_request: I/O error, dev hda, sector 18073246

Is it possible to solve this problem, and rescue the data on the disk, and how will i be able to fix this?

Regards,

Arjan

---

### Post by ajgreeny on 2007-09-24
Can you boot the live CD and check if the disk is mountable and can be read from that.  If so then you can probably get all the files off without too much trouble, but it would be better if someone can possibly help you to get the installed OS booted and running again.

Perhaps worth trying fsck on the partition (when it's unmounted, of course) to see if any repairable faults can be sorted out, and I believe you can do that from the live CD, though you'll need a more detailed explanation because I don't know exactly how it's done.

---

### Post by arjanhs on 2007-09-26
I tried booting with the live cd, that part is working, but it gives a lot of time-outs, i'm still unable to mount the partition, it's the partition mounted to /home, so my home folder is found there with a lot of data, which i don't have backed up.

I will try to use ddrescue and copy the data to an other partition, hope i'm able to get of the data.

Any other suggestions are welcome.

Regards,

Arjan

---

