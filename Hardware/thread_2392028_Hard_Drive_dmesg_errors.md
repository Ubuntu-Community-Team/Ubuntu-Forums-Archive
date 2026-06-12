---
title: "Hard Drive dmesg errors"
date: 2018-05-15
forum: Hardware
---

### Post by pqwoerituytrueiwoq on 2018-05-15
I have tried about 6 sata cables, even bought a very short one today
some times it works without error some times i get a CRC error, sometimes the drive does not appear in the OS, only shows up in the bios maybe 25% of the time
i have tried differnt power cables
at one point i thouth the drive was dead til i put it in a decade old compujter and it worked fine
any ideas on what could be teh problem? maybe a bad solder joint on the HDD?
If the drive is detected it will work properly once the os boots
```
   15.826718] EXT4-fs (sdc1): mounted filesystem with ordered data mode. Opts: (null)
[   15.831134] systemd-journald[279]: Received request to flush runtime journal from PID 1
[   15.849690] EXT4-fs (sdc2): mounted filesystem with ordered data mode. Opts: (null)
[   15.913995] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input14
[   15.914026] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input15
[   15.914054] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input16
[   15.914080] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input17
[   15.919338] EXT4-fs (sdb4): mounted filesystem with ordered data mode. Opts: (null)
[   16.069417] EXT4-fs (sdb2): mounted filesystem with ordered data mode. Opts: (null)
[   16.179990] ata4.00: exception Emask 0x10 SAct 0x7fffffff SErr 0x400100 action 0x6 frozen
[   16.180050] ata4.00: irq_stat 0x08000000, interface fatal error
[   16.180103] ata4: SError: { UnrecovData Handshk }
[   16.180154] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.180208] ata4.00: cmd 61/10:00:9a:53:4d/00:00:00:00:00/40 tag 0 ncq dma 8192 out
                        res 40/00:f4:b2:5b:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.180276] ata4.00: status: { DRDY }
[   16.180325] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.180379] ata4.00: cmd 61/08:08:d2:53:4d/00:00:00:00:00/40 tag 1 ncq dma 4096 out
                        res 40/00:f4:b2:5b:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.180446] ata4.00: status: { DRDY }
[   16.180495] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.180548] ata4.00: cmd 61/08:10:e2:53:4d/00:00:00:00:00/40 tag 2 ncq dma 4096 out
                        res 40/00:f4:b2:5b:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.180616] ata4.00: status: { DRDY }
[   16.180677] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.180742] ata4.00: cmd 61/08:18:02:54:4d/00:00:00:00:00/40 tag 3 ncq dma 4096 out
                        res 40/00:f4:b2:5b:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.180857] ata4.00: status: { DRDY }
[   16.180918] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.180983] ata4.00: cmd 61/08:20:52:54:4d/00:00:00:00:00/40 tag 4 ncq dma 4096 out
                        res 40/00:f4:b2:5b:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.181098] ata4.00: status: { DRDY }
[   16.181159] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.181224] ata4.00: cmd 61/08:28:7a:54:4d/00:00:00:00:00/40 tag 5 ncq dma 4096 out
                        res 40/00:f4:b2:5b:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.181339] ata4.00: status: { DRDY }
[   16.181400] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.181465] ata4.00: cmd 61/08:30:9a:54:4d/00:00:00:00:00/40 tag 6 ncq dma 4096 out
                        res 40/00:f4:b2:5b:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.181580] ata4.00: status: { DRDY }
[   16.181641] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.181706] ata4.00: cmd 61/08:38:b2:54:4d/00:00:00:00:00/40 tag 7 ncq dma 4096 out
                        res 40/00:f4:b2:5b:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.181821] ata4.00: status: { DRDY }
[   16.181882] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.181947] ata4.00: cmd 61/08:40:d2:54:4d/00:00:00:00:00/40 tag 8 ncq dma 4096 out
                        res 40/00:f4:b2:5b:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.182062] ata4.00: status: { DRDY }
[   16.182123] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.182188] ata4.00: cmd 61/10:48:fa:54:4d/00:00:00:00:00/40 tag 9 ncq dma 8192 out
                        res 40/00:f4:b2:5b:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.182303] ata4.00: status: { DRDY }
[   16.182364] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.182430] ata4.00: cmd 61/10:50:42:56:4d/00:00:00:00:00/40 tag 10 ncq dma 8192 out
                        res 40/00:f4:b2:5b:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.182544] ata4.00: status: { DRDY }
[   16.182605] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.182671] ata4.00: cmd 61/10:58:32:57:4d/00:00:00:00:00/40 tag 11 ncq dma 8192 out
                        res 40/00:f4:b2:5b:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.182786] ata4.00: status: { DRDY }
[   16.182847] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.182912] ata4.00: cmd 61/08:60:8a:57:4d/00:00:00:00:00/40 tag 12 ncq dma 4096 out
                        res 40/00:f4:b2:5b:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.183026] ata4.00: status: { DRDY }
[   16.183088] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.183153] ata4.00: cmd 61/10:68:b2:57:4d/00:00:00:00:00/40 tag 13 ncq dma 8192 out
                        res 40/00:f4:b2:5b:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.183268] ata4.00: status: { DRDY }
[   16.183329] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.183394] ata4.00: cmd 61/08:70:0a:58:4d/00:00:00:00:00/40 tag 14 ncq dma 4096 out
                        res 40/00:f4:b2:5b:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.183509] ata4.00: status: { DRDY }
[   16.183570] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.183635] ata4.00: cmd 61/08:78:82:58:4d/00:00:00:00:00/40 tag 15 ncq dma 4096 out
                        res 40/00:f4:b2:5b:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.183750] ata4.00: status: { DRDY }
[   16.183811] ata4.00: failed command: READ FPDMA QUEUED
[   16.183876] ata4.00: cmd 60/18:80:22:80:4f/00:00:00:00:00/40 tag 16 ncq dma 12288 in
                        res 40/00:f4:b2:5b:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.183993] ata4.00: status: { DRDY }
[   16.184054] ata4.00: failed command: READ FPDMA QUEUED
[   16.184119] ata4.00: cmd 60/08:88:22:40:31/00:00:00:00:00/40 tag 17 ncq dma 4096 in
                        res 40/00:f4:b2:5b:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.184234] ata4.00: status: { DRDY }
[   16.184295] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.184360] ata4.00: cmd 61/08:90:92:58:4d/00:00:00:00:00/40 tag 18 ncq dma 4096 out
                        res 40/00:f4:b2:5b:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.184526] ata4.00: status: { DRDY }
[   16.184588] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.184653] ata4.00: cmd 61/08:98:aa:58:4d/00:00:00:00:00/40 tag 19 ncq dma 4096 out
                        res 40/00:f4:b2:5b:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.184768] ata4.00: status: { DRDY }
[   16.184851] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.184927] ata4.00: cmd 61/08:a0:d2:58:4d/00:00:00:00:00/40 tag 20 ncq dma 4096 out
                        res 40/00:f4:b2:5b:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.185075] ata4.00: status: { DRDY }
[   16.185148] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.185225] ata4.00: cmd 61/08:a8:22:59:4d/00:00:00:00:00/40 tag 21 ncq dma 4096 out
                        res 40/00:f4:b2:5b:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.185363] ata4.00: status: { DRDY }
[   16.185364] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.185366] ata4.00: cmd 61/08:b0:7a:59:4d/00:00:00:00:00/40 tag 22 ncq dma 4096 out
                        res 40/00:f4:b2:5b:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.185377] ata4.00: status: { DRDY }
[   16.185378] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.185381] ata4.00: cmd 61/08:b8:92:59:4d/00:00:00:00:00/40 tag 23 ncq dma 4096 out
                        res 40/00:f4:b2:5b:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.185383] ata4.00: status: { DRDY }
[   16.185383] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.185386] ata4.00: cmd 61/08:c0:ca:59:4d/00:00:00:00:00/40 tag 24 ncq dma 4096 out
                        res 40/00:f4:b2:5b:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.185387] ata4.00: status: { DRDY }
[   16.185387] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.185390] ata4.00: cmd 61/08:c8:da:59:4d/00:00:00:00:00/40 tag 25 ncq dma 4096 out
                        res 40/00:f4:b2:5b:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.185391] ata4.00: status: { DRDY }
[   16.185391] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.185394] ata4.00: cmd 61/08:d0:5a:5a:4d/00:00:00:00:00/40 tag 26 ncq dma 4096 out
                        res 40/00:f4:b2:5b:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.185395] ata4.00: status: { DRDY }
[   16.185395] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.185398] ata4.00: cmd 61/08:d8:82:5a:4d/00:00:00:00:00/40 tag 27 ncq dma 4096 out
                        res 40/00:f4:b2:5b:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.185398] ata4.00: status: { DRDY }
[   16.185399] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.185402] ata4.00: cmd 61/08:e0:a2:5a:4d/00:00:00:00:00/40 tag 28 ncq dma 4096 out
                        res 40/00:f4:b2:5b:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.185402] ata4.00: status: { DRDY }
[   16.185403] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.185406] ata4.00: cmd 61/08:e8:ba:5a:4d/00:00:00:00:00/40 tag 29 ncq dma 4096 out
                        res 40/00:f4:b2:5b:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.185406] ata4.00: status: { DRDY }
[   16.185407] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.185410] ata4.00: cmd 61/18:f0:b2:5b:4d/00:00:00:00:00/40 tag 30 ncq dma 12288 out
                        res 40/00:f4:b2:5b:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.185410] ata4.00: status: { DRDY }
[   16.185412] ata4: hard resetting link
[   16.230301] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[   16.303438] EXT4-fs (sdb3): mounted filesystem with ordered data mode. Opts: (null)
[   16.498753] ata4: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[   16.501262] ata4.00: configured for UDMA/133
[   16.501282] ata4: EH complete
[   16.531988] ata4.00: exception Emask 0x10 SAct 0x7ff06003 SErr 0x400100 action 0x6 frozen
[   16.532071] ata4.00: irq_stat 0x08000000, interface fatal error
[   16.532136] ata4: SError: { UnrecovData Handshk }
[   16.532199] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.532264] ata4.00: cmd 61/18:00:7a:5c:4d/00:00:00:00:00/40 tag 0 ncq dma 12288 out
                        res 40/00:0c:72:15:04/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.532379] ata4.00: status: { DRDY }
[   16.532440] ata4.00: failed command: READ FPDMA QUEUED
[   16.537980] ata4.00: cmd 60/08:08:72:15:04/00:00:00:00:00/40 tag 1 ncq dma 4096 in
                        res 40/00:0c:72:15:04/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.538094] ata4.00: status: { DRDY }
[   16.538155] ata4.00: failed command: READ FPDMA QUEUED
[   16.538220] ata4.00: cmd 60/08:68:22:40:31/00:00:00:00:00/40 tag 13 ncq dma 4096 in
                        res 40/00:0c:72:15:04/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.538334] ata4.00: status: { DRDY }
[   16.538395] ata4.00: failed command: READ FPDMA QUEUED
[   16.538459] ata4.00: cmd 60/18:70:22:80:4f/00:00:00:00:00/40 tag 14 ncq dma 12288 in
                        res 40/00:0c:72:15:04/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.538574] ata4.00: status: { DRDY }
[   16.538634] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.538699] ata4.00: cmd 61/10:a0:42:56:4d/00:00:00:00:00/40 tag 20 ncq dma 8192 out
                        res 40/00:0c:72:15:04/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.538813] ata4.00: status: { DRDY }
[   16.538874] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.538939] ata4.00: cmd 61/10:a8:fa:54:4d/00:00:00:00:00/40 tag 21 ncq dma 8192 out
                        res 40/00:0c:72:15:04/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.539053] ata4.00: status: { DRDY }
[   16.539113] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.539178] ata4.00: cmd 61/08:b0:d2:54:4d/00:00:00:00:00/40 tag 22 ncq dma 4096 out
                        res 40/00:0c:72:15:04/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.539292] ata4.00: status: { DRDY }
[   16.539353] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.539418] ata4.00: cmd 61/08:b8:b2:54:4d/00:00:00:00:00/40 tag 23 ncq dma 4096 out
                        res 40/00:0c:72:15:04/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.539532] ata4.00: status: { DRDY }
[   16.539592] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.539657] ata4.00: cmd 61/08:c0:9a:54:4d/00:00:00:00:00/40 tag 24 ncq dma 4096 out
                        res 40/00:0c:72:15:04/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.539771] ata4.00: status: { DRDY }
[   16.539832] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.539897] ata4.00: cmd 61/08:c8:7a:54:4d/00:00:00:00:00/40 tag 25 ncq dma 4096 out
                        res 40/00:0c:72:15:04/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.540013] ata4.00: status: { DRDY }
[   16.540073] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.540138] ata4.00: cmd 61/08:d0:52:54:4d/00:00:00:00:00/40 tag 26 ncq dma 4096 out
                        res 40/00:0c:72:15:04/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.540252] ata4.00: status: { DRDY }
[   16.540313] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.540378] ata4.00: cmd 61/08:d8:02:54:4d/00:00:00:00:00/40 tag 27 ncq dma 4096 out
                        res 40/00:0c:72:15:04/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.540492] ata4.00: status: { DRDY }
[   16.540553] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.540617] ata4.00: cmd 61/08:e0:e2:53:4d/00:00:00:00:00/40 tag 28 ncq dma 4096 out
                        res 40/00:0c:72:15:04/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.540731] ata4.00: status: { DRDY }
[   16.540792] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.540857] ata4.00: cmd 61/08:e8:d2:53:4d/00:00:00:00:00/40 tag 29 ncq dma 4096 out
                        res 40/00:0c:72:15:04/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.540971] ata4.00: status: { DRDY }
[   16.541032] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.541096] ata4.00: cmd 61/10:f0:9a:53:4d/00:00:00:00:00/40 tag 30 ncq dma 8192 out
                        res 40/00:0c:72:15:04/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.541210] ata4.00: status: { DRDY }
[   16.541271] ata4: hard resetting link
[   16.854725] ata4: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[   16.857637] ata4.00: configured for UDMA/133
[   16.857644] ata4: EH complete
[   16.871983] ata4.00: exception Emask 0x10 SAct 0x7ffe0 SErr 0x400100 action 0x6 frozen
[   16.872064] ata4.00: irq_stat 0x08000000, interface fatal error
[   16.872128] ata4: SError: { UnrecovData Handshk }
[   16.872191] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.872256] ata4.00: cmd 61/08:28:d2:53:4d/00:00:00:00:00/40 tag 5 ncq dma 4096 out
                        res 40/00:94:7a:5c:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.872370] ata4.00: status: { DRDY }
[   16.872431] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.872496] ata4.00: cmd 61/08:30:e2:53:4d/00:00:00:00:00/40 tag 6 ncq dma 4096 out
                        res 40/00:94:7a:5c:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.872610] ata4.00: status: { DRDY }
[   16.872671] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.872736] ata4.00: cmd 61/08:38:02:54:4d/00:00:00:00:00/40 tag 7 ncq dma 4096 out
                        res 40/00:94:7a:5c:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.872850] ata4.00: status: { DRDY }
[   16.872910] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.872975] ata4.00: cmd 61/08:40:52:54:4d/00:00:00:00:00/40 tag 8 ncq dma 4096 out
                        res 40/00:94:7a:5c:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.873089] ata4.00: status: { DRDY }
[   16.873149] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.873214] ata4.00: cmd 61/08:48:7a:54:4d/00:00:00:00:00/40 tag 9 ncq dma 4096 out
                        res 40/00:94:7a:5c:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.873328] ata4.00: status: { DRDY }
[   16.873389] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.873454] ata4.00: cmd 61/08:50:9a:54:4d/00:00:00:00:00/40 tag 10 ncq dma 4096 out
                        res 40/00:94:7a:5c:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.873568] ata4.00: status: { DRDY }
[   16.873628] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.873693] ata4.00: cmd 61/08:58:b2:54:4d/00:00:00:00:00/40 tag 11 ncq dma 4096 out
                        res 40/00:94:7a:5c:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.873807] ata4.00: status: { DRDY }
[   16.873868] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.873932] ata4.00: cmd 61/08:60:d2:54:4d/00:00:00:00:00/40 tag 12 ncq dma 4096 out
                        res 40/00:94:7a:5c:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.874047] ata4.00: status: { DRDY }
[   16.874107] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.874172] ata4.00: cmd 61/10:68:fa:54:4d/00:00:00:00:00/40 tag 13 ncq dma 8192 out
                        res 40/00:94:7a:5c:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.874286] ata4.00: status: { DRDY }
[   16.874347] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.874411] ata4.00: cmd 61/10:70:42:56:4d/00:00:00:00:00/40 tag 14 ncq dma 8192 out
                        res 40/00:94:7a:5c:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.874525] ata4.00: status: { DRDY }
[   16.874586] ata4.00: failed command: READ FPDMA QUEUED
[   16.874651] ata4.00: cmd 60/18:78:22:80:4f/00:00:00:00:00/40 tag 15 ncq dma 12288 in
                        res 40/00:94:7a:5c:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.874765] ata4.00: status: { DRDY }
[   16.874826] ata4.00: failed command: READ FPDMA QUEUED
[   16.874890] ata4.00: cmd 60/08:80:22:40:31/00:00:00:00:00/40 tag 16 ncq dma 4096 in
                        res 40/00:94:7a:5c:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.875004] ata4.00: status: { DRDY }
[   16.875065] ata4.00: failed command: READ FPDMA QUEUED
[   16.875130] ata4.00: cmd 60/08:88:72:15:04/00:00:00:00:00/40 tag 17 ncq dma 4096 in
                        res 40/00:94:7a:5c:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.875244] ata4.00: status: { DRDY }
[   16.875304] ata4.00: failed command: WRITE FPDMA QUEUED
[   16.875369] ata4.00: cmd 61/18:90:7a:5c:4d/00:00:00:00:00/40 tag 18 ncq dma 12288 out
                        res 40/00:94:7a:5c:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   16.875483] ata4.00: status: { DRDY }
[   16.875544] ata4: hard resetting link
[   17.190717] ata4: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[   17.193075] ata4.00: configured for UDMA/133
[   17.193081] ata4: EH complete
[   17.207987] ata4: limiting SATA link speed to 3.0 Gbps
[   17.207989] ata4.00: exception Emask 0x10 SAct 0x3fff0 SErr 0x400100 action 0x6 frozen
[   17.208070] ata4.00: irq_stat 0x08000000, interface fatal error
[   17.208134] ata4: SError: { UnrecovData Handshk }
[   17.208196] ata4.00: failed command: WRITE FPDMA QUEUED
[   17.208262] ata4.00: cmd 61/18:20:7a:5c:4d/00:00:00:00:00/40 tag 4 ncq dma 12288 out
                        res 40/00:8c:d2:53:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   17.213459] ata4.00: status: { DRDY }
[   17.213520] ata4.00: failed command: READ FPDMA QUEUED
[   17.213585] ata4.00: cmd 60/08:28:72:15:04/00:00:00:00:00/40 tag 5 ncq dma 4096 in
                        res 40/00:8c:d2:53:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   17.213699] ata4.00: status: { DRDY }
[   17.213760] ata4.00: failed command: READ FPDMA QUEUED
[   17.213824] ata4.00: cmd 60/08:30:22:40:31/00:00:00:00:00/40 tag 6 ncq dma 4096 in
                        res 40/00:8c:d2:53:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   17.213938] ata4.00: status: { DRDY }
[   17.213999] ata4.00: failed command: READ FPDMA QUEUED
[   17.214064] ata4.00: cmd 60/18:38:22:80:4f/00:00:00:00:00/40 tag 7 ncq dma 12288 in
                        res 40/00:8c:d2:53:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   17.214178] ata4.00: status: { DRDY }
[   17.214238] ata4.00: failed command: WRITE FPDMA QUEUED
[   17.214303] ata4.00: cmd 61/10:40:42:56:4d/00:00:00:00:00/40 tag 8 ncq dma 8192 out
                        res 40/00:8c:d2:53:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   17.214417] ata4.00: status: { DRDY }
[   17.214478] ata4.00: failed command: WRITE FPDMA QUEUED
[   17.214543] ata4.00: cmd 61/10:48:fa:54:4d/00:00:00:00:00/40 tag 9 ncq dma 8192 out
                        res 40/00:8c:d2:53:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   17.214657] ata4.00: status: { DRDY }
[   17.214717] ata4.00: failed command: WRITE FPDMA QUEUED
[   17.214782] ata4.00: cmd 61/08:50:d2:54:4d/00:00:00:00:00/40 tag 10 ncq dma 4096 out
                        res 40/00:8c:d2:53:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   17.214896] ata4.00: status: { DRDY }
[   17.214957] ata4.00: failed command: WRITE FPDMA QUEUED
[   17.215022] ata4.00: cmd 61/08:58:b2:54:4d/00:00:00:00:00/40 tag 11 ncq dma 4096 out
                        res 40/00:8c:d2:53:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   17.215136] ata4.00: status: { DRDY }
[   17.215196] ata4.00: failed command: WRITE FPDMA QUEUED
[   17.215261] ata4.00: cmd 61/08:60:9a:54:4d/00:00:00:00:00/40 tag 12 ncq dma 4096 out
                        res 40/00:8c:d2:53:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   17.215375] ata4.00: status: { DRDY }
[   17.215436] ata4.00: failed command: WRITE FPDMA QUEUED
[   17.215501] ata4.00: cmd 61/08:68:7a:54:4d/00:00:00:00:00/40 tag 13 ncq dma 4096 out
                        res 40/00:8c:d2:53:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   17.215615] ata4.00: status: { DRDY }
[   17.215675] ata4.00: failed command: WRITE FPDMA QUEUED
[   17.215740] ata4.00: cmd 61/08:70:52:54:4d/00:00:00:00:00/40 tag 14 ncq dma 4096 out
                        res 40/00:8c:d2:53:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   17.215854] ata4.00: status: { DRDY }
[   17.215915] ata4.00: failed command: WRITE FPDMA QUEUED
[   17.215981] ata4.00: cmd 61/08:78:02:54:4d/00:00:00:00:00/40 tag 15 ncq dma 4096 out
                        res 40/00:8c:d2:53:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   17.216095] ata4.00: status: { DRDY }
[   17.216156] ata4.00: failed command: WRITE FPDMA QUEUED
[   17.216221] ata4.00: cmd 61/08:80:e2:53:4d/00:00:00:00:00/40 tag 16 ncq dma 4096 out
                        res 40/00:8c:d2:53:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   17.216335] ata4.00: status: { DRDY }
[   17.216396] ata4.00: failed command: WRITE FPDMA QUEUED
[   17.216461] ata4.00: cmd 61/08:88:d2:53:4d/00:00:00:00:00/40 tag 17 ncq dma 4096 out
                        res 40/00:8c:d2:53:4d/00:00:00:00:00/40 Emask 0x10 (ATA bus error)
[   17.216575] ata4.00: status: { DRDY }
[   17.216636] ata4: hard resetting link
[   17.530394] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
[   17.532714] ata4.00: configured for UDMA/133
[   17.532720] ata4: EH complete
[   18.294748] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.294749] Bluetooth: BNEP filters: protocol multicast
[   18.294751] Bluetooth: BNEP socket layer initialized
[   18.484347] IPv6: ADDRCONF(NETDEV_UP): enp5s0: link is not ready
[   18.485143] IPv6: ADDRCONF(NETDEV_UP): enp5s0: link is not ready
[   18.487457] IPv6: ADDRCONF(NETDEV_UP): enp6s0: link is not ready
[   18.532156] usb 3-4: reset high-speed USB device number 4 using xhci_hcd
[   18.740428] IPv6: ADDRCONF(NETDEV_UP): enp6s0: link is not ready
[   18.835621] resource sanity check: requesting [mem 0x000c0000-0x000fffff], which spans more than PCI Bus 0000:00 [mem 0x000d0000-0x000d3fff window]
[   18.835722] caller os_map_kernel_space.part.7+0xda/0x120 [nvidia] mapping multiple BARs
[   19.039736] nvidia-modeset: Allocated GPU:0 (GPU-85085171-a57d-b3eb-c5f4-7d771daa684e) @ PCI:0000:01:00.0
[   20.420967] e1000e: enp6s0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[   20.421162] IPv6: ADDRCONF(NETDEV_CHANGE): enp6s0: link becomes ready
[   24.513036] vboxdrv: Found 4 processor cores
[   24.532257] vboxdrv: TSC mode is Invariant, tentative frequency 3498970943 Hz
[   24.532258] vboxdrv: Successfully loaded version 5.2.10_Ubuntu (interface 0x00290001)
[   24.535180] VBoxNetFlt: Successfully started.
[   24.538003] VBoxNetAdp: Successfully started.
[   24.540814] VBoxPciLinuxInit
[   24.542082] vboxpci: IOMMU not found (not registered)
[   26.104236] Bluetooth: RFCOMM TTY layer initialized
[   26.104240] Bluetooth: RFCOMM socket layer initialized
[   26.104243] Bluetooth: RFCOMM ver 1.11
```
*This only happens with this HDD i have other dirves in this system

---

### Post by Autodave on 2018-05-16
Several possibilities. Either the HD is going south, or you still haven't gotten a good cable on it, or (the most likely considering what you have done so far) a bad mother board.

I would try putting the HD onto a cable of one that works. In other words, remove one of the working ones and put this suspect one in its place and see if it works.

---

### Post by pqwoerituytrueiwoq on 2018-05-16
If it were a bad motherboard woun't the issue persist with other drives? my 500gb drive seems work fine

---

### Post by Yellow Pasque on 2018-05-17
What motherboard model? What disk model?

---

### Post by rsteinmetz70112 on 2018-05-17
> **pqwoerituytrueiwoq said:**
> If it were a bad motherboard wounld't the issue persist with other drives? my 500gb drive seems work fine

Not necessarily, it could be just a port or connector on the board. Sometimes if an MB is going bad it will start with one thing then progress.
Have you tried other MB ports? You don't say but I'd guess you have. 
Something else to consider is what the speed of the drives that work and the one that doesn't are. A slower drive may be less susceptible to errors. By speed I'm including the SATA version and other parameters. Also an old computer probably isn't running the drive as fast as it is rated for.

---

### Post by pqwoerituytrueiwoq on 2018-05-19
I only have two sata 3 systems, my laptop (sandy bridge cpu) and my Z97 based desktop
My drive with the issue is doing this (WDC WD10EZEX-21M2NA0):
SATA 3.1, 6.0 Gb/s (current: 1.5 Gb/s)
my good drive is doing this(WDC WD5000AAKX-001CA0):
SATA 3.0, 6.0 Gb/s (current: 3.0 Gb/s)

I have tried all ports on my system including the one that my good drive is on

---

### Post by Autodave on 2018-05-19
Assuming all that, you have to be looking at the HD going bad.

---

### Post by Yellow Pasque on 2018-05-20
Are there any jumpers on the hard disk?

---

### Post by pqwoerituytrueiwoq on 2018-05-20
no jumpers on it

*It passes the 2 hour extended self test

EDIT: The drive seems to work just fine in my neighbors system
and after doing so it now shows: SATA 3.1, 6.0 Gb/s (current: 3.0 Gb/s) on my system
it even appears in the bios again
:-?

EDIT: it looks like ata4 is actually my 500gb drive...
i think i figured out why the drive was running at a low sata speed, that was a bios setting i changed trying to get the drive to show up

---

### Post by pqwoerituytrueiwoq on 2018-05-20
I *think/hope* i got it fixed now
It seems i have been dealing with 2 issues
* bad cable (visible damage caused by side panel)
* bad sata port, [contact cleaner]("https://www.amazon.com/dp/B000BXOGNI") appears to have fixed it, used on both plug and socket (hopefully it stays fixed)
edit: and the issue is back the next day, time for a getto fix: maybe a paper shim will fix it (edit:wait a min that dmesg is yesterday nothing from today...)

---

