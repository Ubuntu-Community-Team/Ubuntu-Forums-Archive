---
title: "ATA vs. ATAPI"
date: 2006-01-29
forum: Hardware &amp; Laptops
---

### Post by tparks on 2006-01-29
After various attempts to burn an audio CD with cdrdao, I read that cdrdao worked better with ATA. When I try cdrecord -scanbus dev=ATA with Breezy, I get a repeated error message, "Error trying to open /dev/hda exclusively," and cdrecord fails to find my DVD-RW drive. If I look for the drive with cdrecord -scanbus dev=ATAPI, however, cdrecord readily finds it.

On another machine running Debian stable with an upgraded 2.6 kernel, using "dev=ATA" works. I can burn audio cds if I specify dev=ATA on the Debian machine. But cdrdao starts and then fails using dev=ATAPI on the Ubuntu box.

Two questions:
1) What is the difference between ATA and ATAPI?

2) How can I get Ubuntu to accept the dev=ATA option with cdrecord and cdrdao (e.g. cdrdao write --device ATA:0,0,0 cdname.toc)?

Thanks,
Ted Parks

---

