---
title: "CDRom won't work.."
date: 2010-01-19
forum: Hardware
---

### Post by rainy-day on 2010-01-19
Hi, I have 9.10 and my cdrom doesn't work. About 2-3 months ago I had some issues with burning dvds and I was messing with cdrom device files in /dev/ and I don't remember what I did exactly but I think now I need some method to restore or re-create these device files. I was too busy at the time to look into this further and now unfortunately I don't remember what exactly I did. Now the issue is simply that when I put the cd in the cd drive, it doesn't show up in nautilus or, well, anywhere. In /media/, I have this:

lrwxrwxrwx 1 root root     6 2009-03-07 17:57 cdrom -> cdrom0
drwxr-xr-x 2 root root  4096 2009-03-07 17:57 cdrom0

But actually the problem might be something else, I just found this in dmesg output:

[    4.064501] ata7.00: ATAPI: TSSTcorpCD/DVDW SH-S182M, SB03, max UDMA/33
[    9.064052] ata7.01: qc timeout (cmd 0x27)
[    9.064059] ata7.01: failed to read native max address (err_mask=0x4)
[   19.228040] ata7.01: qc timeout (cmd 0x27)
[   19.228046] ata7.01: failed to read native max address (err_mask=0x4)
[   19.228049] ata7.01: revalidation failed (errno=-5)
[   29.392043] ata7.01: qc timeout (cmd 0x27)
[   29.392049] ata7.01: failed to read native max address (err_mask=0x4)
[   29.392051] ata7.01: revalidation failed (errno=-5)
[   29.392085] ata7.01: disabled
[   29.392088] ata7.00: failed to IDENTIFY (I/O error, err_mask=0x40)
[   29.392090] ata7.00: revalidation failed (errno=-5)
[   29.572515] ata7.00: configured for UDMA/33
[   34.572041] ata7.00: qc timeout (cmd 0xa0)
[   34.572048] ata7.00: TEST_UNIT_READY failed (err_mask=0x4)
[   34.572050] ata7.00: limiting speed to UDMA/33:PIO3
[   34.752515] ata7.00: configured for UDMA/33
[   39.752030] ata7.00: qc timeout (cmd 0xa0)
[   39.752036] ata7.00: TEST_UNIT_READY failed (err_mask=0x4)
[   39.752038] ata7.00: disabled
[   39.752060] ata7: soft resetting link
[   39.908099] ata7: EH complete

Also: there is no /dev/dvd at all.

The drive does work in windows just fine (which I dual-boot).

Thanks!

---

### Post by rainy-day on 2010-01-20
I looked at fstab and here's what I have there:
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

I don't have any /dev/scd* at all.

I've also upgraded to ubuntu 9.10 and to new kernel and now there's a small difference in dmesg, ata7.01 is NOT disabled but still gets timeouts and 'failed to read native max address':

[    0.788993] ata7: PATA max UDMA/100 cmd 0xb000 ctl 0xb100 bmdma 0xb400 irq 19
[    0.968505] ata7.00: ATAPI: TSSTcorpCD/DVDW SH-S182M, SB03, max UDMA/33
[    5.968040] ata7.01: qc timeout (cmd 0x27)
[    5.968047] ata7.01: failed to read native max address (err_mask=0x4)
[   16.140038] ata7.01: qc timeout (cmd 0x27)
[   16.140045] ata7.01: failed to read native max address (err_mask=0x4)
[   26.312035] ata7.01: qc timeout (cmd 0x27)
[   26.312042] ata7.01: failed to read native max address (err_mask=0x4)
[   26.492518] ata7.00: configured for UDMA/33
[   31.492025] ata7.00: qc timeout (cmd 0xa0)
[   31.492032] ata7.00: TEST_UNIT_READY failed (err_mask=0x4)
[   31.672517] ata7.00: configured for UDMA/33
[   36.672025] ata7.00: qc timeout (cmd 0xa0)
[   36.672032] ata7.00: TEST_UNIT_READY failed (err_mask=0x4)
[   36.672035] ata7.00: limiting speed to UDMA/33:PIO3
[   36.852517] ata7.00: configured for UDMA/33
[   41.852033] ata7.00: qc timeout (cmd 0xa0)
[   41.852041] ata7.00: TEST_UNIT_READY failed (err_mask=0x4)
[   41.852043] ata7.00: disabled
[   41.852071] ata7: soft resetting link
[   47.016043] ata7.01: qc timeout (cmd 0x27)
[   47.016051] ata7.01: failed to read native max address (err_mask=0x4)
[   47.016069] ata7: soft resetting link
[   57.180043] ata7.01: qc timeout (cmd 0x27)
[   57.180050] ata7.01: failed to read native max address (err_mask=0x4)
[   57.180069] ata7: soft resetting link
[   67.344041] ata7.01: qc timeout (cmd 0x27)
[   67.344049] ata7.01: failed to read native max address (err_mask=0x4)
[   67.344067] ata7: soft resetting link
[   67.500104] ata7: EH complete

---

### Post by rainy-day on 2010-01-20
Sorry, I just realized I didn't say anything about what kind of system this is, it's a pretty standard ~1.5 years old system with a dual core cpu, pretty good motherboard, probably asus or tyan or msi, and the cdrom itself is a samsung dvd-rw. I did use it with ubuntu before and it worked fine, both for reading and burning cds/dvds.

---

