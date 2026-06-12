---
title: "cdrom hell"
date: 2005-08-19
forum: Hardware &amp; Laptops
---

### Post by unixpusher on 2005-08-19
Hi,

I switched from mandrake to ubuntu, i'm starting to wonder how good of an idea that was...right now, I got 2 issues with my cdrom/dvd burner

1) Slow tranfers speed. I have found a lot of post regarding this issue, nothing that fixed my problem. I tried the following:

turning on dma using hdparm , hdparm says it's enabled...
laoding the amd74xx and ide-core before ide-cd using/etc/modules
tried different disk medium just in case ...

It still transfers only at 2-3 MB/s ... worked fine on mandrake...
the cdrom drive doesn't even speed up, it stays super quiet... like it's forced to operate at low speed
hell, i even tried hdparm -E48 and hdparm -x66 ... it just don't work ...
I hear something being compiled in the stock kernel to keep cdrom drive to use dma, if that's the case
how can anyone get it to work with the tips i read unless they recompiled the kernel ?

2) that piece of shit gam_server keeps files open on the cdrom even after i close every apps... i have to kill it to be able to umount the device... who cares about fam !#$? i can't find an init script to disable it... never had this problem in mandrake while using kde, what's happeening ?


Thanks to anyone who can help me get my cdrom drive to work like it should...

---

### Post by heimo on 2005-08-19
People who have compiled kernel to solve this issue, do it to force DMA on. You could try older or latest kernel, but not because of forcing DMA on. Also I would try to change the drive to different contoller / channel, if it's now master on secondary, try slave on primary (if possible). I assume you have checked BIOS settings? Are those all on auto (access mode)?

---

