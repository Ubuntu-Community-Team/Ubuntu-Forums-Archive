---
title: "NUC 10i3FNH2 / Samsung 860 EVO Drives and Ubuntu 20.04.2 IO Errors"
date: 2021-03-07
forum: Hardware
---

### Post by br1c3.s1m0n on 2021-03-07
Hi, 


I'm havving an issue with newly bought Intel NUC 10i3FNH2 / Samsung SSD 860 EVO (500GB and 1TB) / Ubuntu 20.04.2


Basically the kernel keeps on spiiting out I/O error messages as follows



```

[Sun Mar  7 14:58:21 2021] ata3: hard resetting link
[Sun Mar  7 14:58:21 2021] ata3: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[Sun Mar  7 14:58:21 2021] ata3.00: supports DRM functions and may not be fully accessible
[Sun Mar  7 14:58:21 2021] ata3.00: supports DRM functions and may not be fully accessible
[Sun Mar  7 14:58:21 2021] ata3.00: configured for UDMA/133
[Sun Mar  7 14:58:21 2021] ata3: EH complete
[Sun Mar  7 14:58:21 2021] ata3.00: Enabling discard_zeroes_data
[Sun Mar  7 14:58:21 2021] ata3.00: exception Emask 0x10 SAct 0x4100000f SErr 0x400100 action 0x6 frozen
[Sun Mar  7 14:58:21 2021] ata3.00: irq_stat 0x08000000, interface fatal error
[Sun Mar  7 14:58:21 2021] ata3: SError: { UnrecovData Handshk }
[Sun Mar  7 14:58:21 2021] ata3.00: failed command: WRITE FPDMA QUEUED
[Sun Mar  7 14:58:21 2021] ata3.00: cmd 61/50:00:88:68:f1/00:00:00:00:00/40 tag 0 ncq dma 40960 out
[Sun Mar  7 14:58:21 2021] ata3.00: status: { DRDY }
[Sun Mar  7 14:58:21 2021] ata3.00: failed command: WRITE FPDMA QUEUED
[Sun Mar  7 14:58:21 2021] ata3.00: cmd 61/10:08:e0:68:f1/00:00:00:00:00/40 tag 1 ncq dma 8192 out
[Sun Mar  7 14:58:21 2021] ata3.00: status: { DRDY }
[Sun Mar  7 14:58:21 2021] ata3.00: failed command: WRITE FPDMA QUEUED
[Sun Mar  7 14:58:21 2021] ata3.00: cmd 61/10:10:f8:68:f1/00:00:00:00:00/40 tag 2 ncq dma 8192 out
[Sun Mar  7 14:58:21 2021] ata3.00: status: { DRDY }
[Sun Mar  7 14:58:21 2021] ata3.00: failed command: WRITE FPDMA QUEUED
[Sun Mar  7 14:58:21 2021] ata3.00: cmd 61/30:18:18:69:f1/00:00:00:00:00/40 tag 3 ncq dma 24576 out
[Sun Mar  7 14:58:21 2021] ata3.00: status: { DRDY }
[Sun Mar  7 14:58:21 2021] ata3.00: failed command: READ FPDMA QUEUED
[Sun Mar  7 14:58:21 2021] ata3.00: cmd 60/08:c0:a8:ff:75/00:00:04:00:00/40 tag 24 ncq dma 4096 in
[Sun Mar  7 14:58:21 2021] ata3.00: status: { DRDY }
[Sun Mar  7 14:58:21 2021] ata3.00: failed command: WRITE FPDMA QUEUED
[Sun Mar  7 14:58:21 2021] ata3.00: cmd 61/28:f0:58:68:f1/00:00:00:00:00/40 tag 30 ncq dma 20480 out
[Sun Mar  7 14:58:21 2021] ata3.00: status: { DRDY }
[Sun Mar  7 14:58:21 2021] ata3: hard resetting link
[Sun Mar  7 14:58:21 2021] ata3: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[Sun Mar  7 14:58:21 2021] ata3.00: supports DRM functions and may not be fully accessible
[Sun Mar  7 14:58:21 2021] ata3.00: supports DRM functions and may not be fully accessible
[Sun Mar  7 14:58:21 2021] ata3.00: configured for UDMA/133
[Sun Mar  7 14:58:21 2021] ata3: EH complete
[Sun Mar  7 14:58:21 2021] ata3.00: Enabling discard_zeroes_data
[...]

[Sun Mar  7 14:58:22 2021] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[...]
[Sun Mar  7 14:58:27 2021] ata3: limiting SATA link speed to 3.0 Gbps
[Sun Mar  7 14:58:27 2021] ata3.00: exception Emask 0x10 SAct 0x800 SErr 0x400100 action 0x6 frozen
[Sun Mar  7 14:58:27 2021] ata3.00: irq_stat 0x08000000, interface fatal error
[Sun Mar  7 14:58:27 2021] ata3: SError: { UnrecovData Handshk }
[Sun Mar  7 14:58:27 2021] ata3.00: failed command: WRITE FPDMA QUEUED
[Sun Mar  7 14:58:27 2021] ata3.00: cmd 61/d8:58:90:10:b4/01:00:0c:00:00/40 tag 11 ncq dma 241664 out
[Sun Mar  7 14:58:27 2021] ata3.00: status: { DRDY }
[Sun Mar  7 14:58:27 2021] ata3: hard resetting link
[Sun Mar  7 14:58:27 2021] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
[Sun Mar  7 14:58:27 2021] ata3.00: supports DRM functions and may not be fully accessible
[Sun Mar  7 14:58:27 2021] ata3.00: supports DRM functions and may not be fully accessible
[Sun Mar  7 14:58:27 2021] ata3.00: configured for UDMA/133
[Sun Mar  7 14:58:27 2021] ata3: EH complete
[Sun Mar  7 14:58:27 2021] ata3.00: Enabling discard_zeroes_data
```





So far I have:


- Updated NUC Bios to FNCML357
- Updated Samsung Disks FW to RVT04B6Q
- Updated Ubuntu 20.04 w/ Kernel 5.4.0-66-generic
- Tried on two different NUC servers
- Tried w/ two differnt Samsung drives (1TB and 500G)
- Tried differnet power settings on the NUC (and attempted to disabled m2 and SDHC slots)
- Tried a fresh install of Ubuntu 20.04.2


But the error messages keep on going.

Any ides where I could be looking now?




Pleaase help!




Cheers,


Brice.

---

### Post by mastablasta on 2021-03-10
> **br1c3.s1m0n said:**
> H
- Tried w/ two differnt Samsung drives (1TB and 500G)

drive is not the issue then. looks very much like connection issue (unless some kernel bug is causing it - similar specific cases). it can be faulty sata controller or SATA cable. check connections. have you tried replacing the SATA cable yet? can you replace it? connectors could also be faulty.

see a similar issue here: 
[https://unix.stackexchange.com/questions/123064/possible-issues-with-ssd-sata3-drive](https://unix.stackexchange.com/questions/123064/possible-issues-with-ssd-sata3-drive)

i wonder if you could try with nvme drive (if NUC has the space for it)

---

### Post by br1c3.s1m0n on 2021-03-11
Hi, 

Thanks for your reply! Much appreciated.
 
Unfortunately I have tried with two different (brand new) NUC units and on two different Samsung Drives (both 860 EVO) with the same issue. Thus it seems to me quite unlikely that this could be related to a hardware fault. I have also installed a Samsung NVME drive and the issue did not occur (but I suspect queued TRIM does is not implemented the same way on NVME drives than on SATA SSD).
 
I have also contacted Samsung who have been helpless so far and have investigated the following posts:
[URL="https://bugzilla.kernel.org/show_bug.cgi?id=203475"]
[/URL][https://bugzilla.kernel.org/show_bug.cgi?id=203475](https://bugzilla.kernel.org/show_bug.cgi?id=203475)
[https://bugzilla.kernel.org/show_bug.cgi?id=72341]("https://bugzilla.kernel.org/show_bug.cgi?id=203475")

I have a feeling the issue lies with Samsung Drives not being able to perform queued TRIM commands due to an incorrect NCQ implementation in their firmware.

All I can try now is to push them to update their FW should they acknowledge that the issue lies with them.

But if you have any other ides I'm all ears! :-)



Cheers,

B.

---

### Post by Yellow Pasque on 2021-03-11
Did you try disabling NCQ? (boot with libata.force=noncq kernel parameter)

---

### Post by br1c3.s1m0n on 2021-03-12
Hi, 

Yes I did (through sysctl) and the errors have gone away. However performance wise it sucks. 

No need to mention that it's a bit of a bummer to buy an SSD where NCQ is not properly implemented. 

Also Samsung claim that it works w/ Windows (which bugs me even more!)

Cheers,

B.

---

### Post by CelticWarrior on 2021-03-12
I suspect that M.2 won't have the same problem.

---

