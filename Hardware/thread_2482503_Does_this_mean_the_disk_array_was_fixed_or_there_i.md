---
title: "Does this mean the disk array was fixed or there is a issue"
date: 2023-01-02
forum: Hardware
---

### Post by pqwoerituytrueiwoq on 2023-01-02
Yesterday i noticed some com errors for 2 of my drives 

powered it down and used some contact cleaner and everything seemed fine

checked today and found this in dmesg

```
[63854.882728] md: data-check of RAID array md2
[65043.542352] ata10.00: exception Emask 0x10 SAct 0xffffffff SErr 0xb80100 action 0x6
[65043.544013] ata10.00: irq_stat 0x08000000
[65043.545651] ata10: SError: { UnrecovData 10B8B Dispar BadCRC LinkSeq }
[65043.547301] ata10.00: failed command: READ FPDMA QUEUED
[65043.548919] ata10.00: cmd 60/80:00:80:0a:94/00:00:34:01:00/40 tag 0 ncq dma 65536 in
                        res 40/00:38:80:18:94/00:00:34:01:00/40 Emask 0x10 (ATA bus error)
[65043.552237] ata10.00: status: { DRDY }
[65043.553890] ata10.00: failed command: READ FPDMA QUEUED
[65043.555549] ata10.00: cmd 60/00:08:00:0b:94/01:00:34:01:00/40 tag 1 ncq dma 131072 in
                        res 40/00:38:80:18:94/00:00:34:01:00/40 Emask 0x10 (ATA bus error)
[65043.558933] ata10.00: status: { DRDY }
[65043.560632] ata10.00: failed command: READ FPDMA QUEUED
[65043.562354] ata10.00: cmd 60/00:10:00:0c:94/04:00:34:01:00/40 tag 2 ncq dma 524288 in
                        res 40/00:38:80:18:94/00:00:34:01:00/40 Emask 0x10 (ATA bus error)
[65043.565845] ata10.00: status: { DRDY }
[65043.567599] ata10.00: failed command: READ FPDMA QUEUED
[65043.569351] ata10.00: cmd 60/80:18:00:10:94/02:00:34:01:00/40 tag 3 ncq dma 327680 in
                        res 40/00:38:80:18:94/00:00:34:01:00/40 Emask 0x10 (ATA bus error)
[65043.572907] ata10.00: status: { DRDY }
[65043.574692] ata10.00: failed command: READ FPDMA QUEUED
[65043.576477] ata10.00: cmd 60/80:20:80:12:94/01:00:34:01:00/40 tag 4 ncq dma 196608 in
                        res 40/00:38:80:18:94/00:00:34:01:00/40 Emask 0x10 (ATA bus error)
[65043.580146] ata10.00: status: { DRDY }
[65043.581974] ata10.00: failed command: READ FPDMA QUEUED
[65043.583825] ata10.00: cmd 60/00:28:00:14:94/04:00:34:01:00/40 tag 5 ncq dma 524288 in
                        res 40/00:38:80:18:94/00:00:34:01:00/40 Emask 0x10 (ATA bus error)
[65043.587613] ata10.00: status: { DRDY }
[65043.589510] ata10.00: failed command: READ FPDMA QUEUED
[65043.591427] ata10.00: cmd 60/80:30:00:18:94/00:00:34:01:00/40 tag 6 ncq dma 65536 in
                        res 40/00:38:80:18:94/00:00:34:01:00/40 Emask 0x10 (ATA bus error)
[65043.595311] ata10.00: status: { DRDY }
[65043.597263] ata10.00: failed command: READ FPDMA QUEUED
[65043.599209] ata10.00: cmd 60/80:38:80:18:94/02:00:34:01:00/40 tag 7 ncq dma 327680 in
                        res 40/00:38:80:18:94/00:00:34:01:00/40 Emask 0x10 (ATA bus error)
[65043.603106] ata10.00: status: { DRDY }
[65043.605056] ata10.00: failed command: READ FPDMA QUEUED
[65043.607008] ata10.00: cmd 60/80:40:00:1b:94/00:00:34:01:00/40 tag 8 ncq dma 65536 in
                        res 40/00:38:80:18:94/00:00:34:01:00/40 Emask 0x10 (ATA bus error)
[65043.610954] ata10.00: status: { DRDY }
[65043.612885] ata10.00: failed command: READ FPDMA QUEUED
[65043.614821] ata10.00: cmd 60/00:48:00:bc:93/04:00:34:01:00/40 tag 9 ncq dma 524288 in
                        res 40/00:38:80:18:94/00:00:34:01:00/40 Emask 0x10 (ATA bus error)
[65043.618698] ata10.00: status: { DRDY }
[65043.620602] ata10.00: failed command: READ FPDMA QUEUED
[65043.622527] ata10.00: cmd 60/00:50:00:c0:93/04:00:34:01:00/40 tag 10 ncq dma 524288 in
                        res 40/00:38:80:18:94/00:00:34:01:00/40 Emask 0x10 (ATA bus error)
[65043.625492] ata10.00: status: { DRDY }
[65043.626824] ata10.00: failed command: READ FPDMA QUEUED
[65043.628049] ata10.00: cmd 60/80:58:00:c4:93/03:00:34:01:00/40 tag 11 ncq dma 458752 in
                        res 40/00:38:80:18:94/00:00:34:01:00/40 Emask 0x10 (ATA bus error)
[65043.629750] ata10.00: status: { DRDY }
[65043.630603] ata10.00: failed command: READ FPDMA QUEUED
[65043.631438] ata10.00: cmd 60/80:60:80:c7:93/01:00:34:01:00/40 tag 12 ncq dma 196608 in
                        res 40/00:38:80:18:94/00:00:34:01:00/40 Emask 0x10 (ATA bus error)
[65043.633111] ata10.00: status: { DRDY }
[65043.633953] ata10.00: failed command: READ FPDMA QUEUED
[65043.634795] ata10.00: cmd 60/00:68:00:c9:93/03:00:34:01:00/40 tag 13 ncq dma 393216 in
                        res 40/00:38:80:18:94/00:00:34:01:00/40 Emask 0x10 (ATA bus error)
[65043.636507] ata10.00: status: { DRDY }
[65043.637368] ata10.00: failed command: READ FPDMA QUEUED
[65043.638230] ata10.00: cmd 60/00:70:00:cc:93/06:00:34:01:00/40 tag 14 ncq dma 786432 in
                        res 40/00:38:80:18:94/00:00:34:01:00/40 Emask 0x10 (ATA bus error)
[65043.639980] ata10.00: status: { DRDY }
[65043.640857] ata10.00: failed command: READ FPDMA QUEUED
[65043.641723] ata10.00: cmd 60/00:78:00:d2:93/06:00:34:01:00/40 tag 15 ncq dma 786432 in
                        res 40/00:38:80:18:94/00:00:34:01:00/40 Emask 0x10 (ATA bus error)
[65043.643462] ata10.00: status: { DRDY }
[65043.644326] ata10.00: failed command: READ FPDMA QUEUED
[65043.645187] ata10.00: cmd 60/00:80:00:d8:93/04:00:34:01:00/40 tag 16 ncq dma 524288 in
                        res 40/00:38:80:18:94/00:00:34:01:00/40 Emask 0x10 (ATA bus error)
[65043.646923] ata10.00: status: { DRDY }
[65043.647788] ata10.00: failed command: READ FPDMA QUEUED
[65043.648649] ata10.00: cmd 60/00:88:00:dc:93/04:00:34:01:00/40 tag 17 ncq dma 524288 in
                        res 40/00:38:80:18:94/00:00:34:01:00/40 Emask 0x10 (ATA bus error)
[65043.650386] ata10.00: status: { DRDY }
[65043.651252] ata10.00: failed command: READ FPDMA QUEUED
[65043.652113] ata10.00: cmd 60/80:90:00:e0:93/03:00:34:01:00/40 tag 18 ncq dma 458752 in
                        res 40/00:38:80:18:94/00:00:34:01:00/40 Emask 0x10 (ATA bus error)
[65043.653847] ata10.00: status: { DRDY }
[65043.654715] ata10.00: failed command: READ FPDMA QUEUED
[65043.655577] ata10.00: cmd 60/00:98:80:e3:93/01:00:34:01:00/40 tag 19 ncq dma 131072 in
                        res 40/00:38:80:18:94/00:00:34:01:00/40 Emask 0x10 (ATA bus error)
[65043.657311] ata10.00: status: { DRDY }
[65043.658177] ata10.00: failed command: READ FPDMA QUEUED
[65043.659042] ata10.00: cmd 60/00:a0:80:e4:93/03:00:34:01:00/40 tag 20 ncq dma 393216 in
                        res 40/00:38:80:18:94/00:00:34:01:00/40 Emask 0x10 (ATA bus error)
[65043.660776] ata10.00: status: { DRDY }
[65043.661641] ata10.00: failed command: READ FPDMA QUEUED
[65043.662506] ata10.00: cmd 60/00:a8:00:e8:93/04:00:34:01:00/40 tag 21 ncq dma 524288 in
                        res 40/00:38:80:18:94/00:00:34:01:00/40 Emask 0x10 (ATA bus error)
[65043.664241] ata10.00: status: { DRDY }
[65043.665107] ata10.00: failed command: READ FPDMA QUEUED
[65043.665969] ata10.00: cmd 60/00:b0:00:ec:93/08:00:34:01:00/40 tag 22 ncq dma 1048576 in
                        res 40/00:38:80:18:94/00:00:34:01:00/40 Emask 0x10 (ATA bus error)
[65043.667708] ata10.00: status: { DRDY }
[65043.668575] ata10.00: failed command: READ FPDMA QUEUED
[65043.669437] ata10.00: cmd 60/80:b8:00:f4:93/03:00:34:01:00/40 tag 23 ncq dma 458752 in
                        res 40/00:38:80:18:94/00:00:34:01:00/40 Emask 0x10 (ATA bus error)
[65043.671176] ata10.00: status: { DRDY }
[65043.672043] ata10.00: failed command: READ FPDMA QUEUED
[65043.672905] ata10.00: cmd 60/00:c0:80:f7:93/01:00:34:01:00/40 tag 24 ncq dma 131072 in
                        res 40/00:38:80:18:94/00:00:34:01:00/40 Emask 0x10 (ATA bus error)
[65043.674645] ata10.00: status: { DRDY }
[65043.675511] ata10.00: failed command: READ FPDMA QUEUED
[65043.676374] ata10.00: cmd 60/80:c8:80:f8:93/03:00:34:01:00/40 tag 25 ncq dma 458752 in
                        res 40/00:38:80:18:94/00:00:34:01:00/40 Emask 0x10 (ATA bus error)
[65043.678112] ata10.00: status: { DRDY }
[65043.678982] ata10.00: failed command: READ FPDMA QUEUED
[65043.679845] ata10.00: cmd 60/80:d0:00:fc:93/03:00:34:01:00/40 tag 26 ncq dma 458752 in
                        res 40/00:38:80:18:94/00:00:34:01:00/40 Emask 0x10 (ATA bus error)
[65043.681580] ata10.00: status: { DRDY }
[65043.682448] ata10.00: failed command: READ FPDMA QUEUED
[65043.683309] ata10.00: cmd 60/80:d8:80:ff:93/00:00:34:01:00/40 tag 27 ncq dma 65536 in
                        res 40/00:38:80:18:94/00:00:34:01:00/40 Emask 0x10 (ATA bus error)
[65043.685044] ata10.00: status: { DRDY }
[65043.685909] ata10.00: failed command: READ FPDMA QUEUED
[65043.686773] ata10.00: cmd 60/80:e0:00:00:94/06:00:34:01:00/40 tag 28 ncq dma 851968 in
                        res 40/00:38:80:18:94/00:00:34:01:00/40 Emask 0x10 (ATA bus error)
[65043.688506] ata10.00: status: { DRDY }
[65043.689371] ata10.00: failed command: READ FPDMA QUEUED
[65043.690235] ata10.00: cmd 60/80:e8:80:06:94/01:00:34:01:00/40 tag 29 ncq dma 196608 in
                        res 40/00:38:80:18:94/00:00:34:01:00/40 Emask 0x10 (ATA bus error)
[65043.691970] ata10.00: status: { DRDY }
[65043.692835] ata10.00: failed command: READ FPDMA QUEUED
[65043.693696] ata10.00: cmd 60/80:f0:00:08:94/02:00:34:01:00/40 tag 30 ncq dma 327680 in
                        res 40/00:38:80:18:94/00:00:34:01:00/40 Emask 0x10 (ATA bus error)
[65043.695434] ata10.00: status: { DRDY }
[65043.696299] ata10.00: failed command: READ FPDMA QUEUED
[65043.697160] ata10.00: cmd 60/80:f8:80:e7:93/00:00:34:01:00/40 tag 31 ncq dma 65536 in
                        res 40/00:38:80:18:94/00:00:34:01:00/40 Emask 0x10 (ATA bus error)
[65043.698896] ata10.00: status: { DRDY }
[65043.699764] ata10: hard resetting link
[65044.170671] ata10: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[65044.172883] ata10.00: configured for UDMA/133
[65044.172995] ata10: EH complete
[65913.626966] ata13.00: exception Emask 0x2 SAct 0xffffffff SErr 0x400 action 0x6
[65913.628963] ata13.00: irq_stat 0x08000000
[65913.630902] ata13: SError: { Proto }
[65913.632840] ata13.00: failed command: READ FPDMA QUEUED
[65913.634761] ata13.00: cmd 60/00:00:00:c0:e3/04:00:3e:01:00/40 tag 0 ncq dma 524288 in
                        res 40/00:80:00:84:e3/00:00:3e:01:00/40 Emask 0x2 (HSM violation)
[65913.638618] ata13.00: status: { DRDY }
[65913.640524] ata13.00: failed command: READ FPDMA QUEUED
[65913.642432] ata13.00: cmd 60/00:08:00:c4:e3/04:00:3e:01:00/40 tag 1 ncq dma 524288 in
                        res 40/00:80:00:84:e3/00:00:3e:01:00/40 Emask 0x2 (HSM violation)
[65913.646281] ata13.00: status: { DRDY }
[65913.648185] ata13.00: failed command: READ FPDMA QUEUED
[65913.650092] ata13.00: cmd 60/00:10:00:c8:e3/04:00:3e:01:00/40 tag 2 ncq dma 524288 in
                        res 40/00:80:00:84:e3/00:00:3e:01:00/40 Emask 0x2 (HSM violation)
[65913.653937] ata13.00: status: { DRDY }
[65913.655837] ata13.00: failed command: READ FPDMA QUEUED
[65913.657742] ata13.00: cmd 60/00:18:00:cc:e3/04:00:3e:01:00/40 tag 3 ncq dma 524288 in
                        res 40/00:80:00:84:e3/00:00:3e:01:00/40 Emask 0x2 (HSM violation)
[65913.661581] ata13.00: status: { DRDY }
[65913.663480] ata13.00: failed command: READ FPDMA QUEUED
[65913.665384] ata13.00: cmd 60/00:20:00:d0:e3/04:00:3e:01:00/40 tag 4 ncq dma 524288 in
                        res 40/00:80:00:84:e3/00:00:3e:01:00/40 Emask 0x2 (HSM violation)
[65913.669220] ata13.00: status: { DRDY }
[65913.671118] ata13.00: failed command: READ FPDMA QUEUED
[65913.673019] ata13.00: cmd 60/00:28:00:d4:e3/04:00:3e:01:00/40 tag 5 ncq dma 524288 in
                        res 40/00:80:00:84:e3/00:00:3e:01:00/40 Emask 0x2 (HSM violation)
[65913.676853] ata13.00: status: { DRDY }
[65913.678746] ata13.00: failed command: READ FPDMA QUEUED
[65913.680650] ata13.00: cmd 60/00:30:00:d8:e3/04:00:3e:01:00/40 tag 6 ncq dma 524288 in
                        res 40/00:80:00:84:e3/00:00:3e:01:00/40 Emask 0x2 (HSM violation)
[65913.684480] ata13.00: status: { DRDY }
[65913.686371] ata13.00: failed command: READ FPDMA QUEUED
[65913.688272] ata13.00: cmd 60/00:38:00:dc:e3/04:00:3e:01:00/40 tag 7 ncq dma 524288 in
                        res 40/00:80:00:84:e3/00:00:3e:01:00/40 Emask 0x2 (HSM violation)
[65913.692099] ata13.00: status: { DRDY }
[65913.693990] ata13.00: failed command: READ FPDMA QUEUED
[65913.695892] ata13.00: cmd 60/00:40:00:e0:e3/04:00:3e:01:00/40 tag 8 ncq dma 524288 in
                        res 40/00:80:00:84:e3/00:00:3e:01:00/40 Emask 0x2 (HSM violation)
[65913.699720] ata13.00: status: { DRDY }
[65913.701612] ata13.00: failed command: READ FPDMA QUEUED
[65913.703513] ata13.00: cmd 60/00:48:00:e4:e3/04:00:3e:01:00/40 tag 9 ncq dma 524288 in
                        res 40/00:80:00:84:e3/00:00:3e:01:00/40 Emask 0x2 (HSM violation)
[65913.707342] ata13.00: status: { DRDY }
[65913.708912] ata13.00: failed command: READ FPDMA QUEUED
[65913.710238] ata13.00: cmd 60/00:50:00:e8:e3/04:00:3e:01:00/40 tag 10 ncq dma 524288 in
                        res 40/00:80:00:84:e3/00:00:3e:01:00/40 Emask 0x2 (HSM violation)
[65913.712910] ata13.00: status: { DRDY }
[65913.714198] ata13.00: failed command: READ FPDMA QUEUED
[65913.715055] ata13.00: cmd 60/00:58:00:ec:e3/04:00:3e:01:00/40 tag 11 ncq dma 524288 in
                        res 40/00:80:00:84:e3/00:00:3e:01:00/40 Emask 0x2 (HSM violation)
[65913.716772] ata13.00: status: { DRDY }
[65913.717630] ata13.00: failed command: READ FPDMA QUEUED
[65913.718481] ata13.00: cmd 60/00:60:00:f0:e3/04:00:3e:01:00/40 tag 12 ncq dma 524288 in
                        res 40/00:80:00:84:e3/00:00:3e:01:00/40 Emask 0x2 (HSM violation)
[65913.720199] ata13.00: status: { DRDY }
[65913.721048] ata13.00: failed command: READ FPDMA QUEUED
[65913.721899] ata13.00: cmd 60/00:68:00:f4:e3/04:00:3e:01:00/40 tag 13 ncq dma 524288 in
                        res 40/00:80:00:84:e3/00:00:3e:01:00/40 Emask 0x2 (HSM violation)
[65913.723615] ata13.00: status: { DRDY }
[65913.724472] ata13.00: failed command: READ FPDMA QUEUED
[65913.725332] ata13.00: cmd 60/00:70:00:f8:e3/04:00:3e:01:00/40 tag 14 ncq dma 524288 in
                        res 40/00:80:00:84:e3/00:00:3e:01:00/40 Emask 0x2 (HSM violation)
[65913.727048] ata13.00: status: { DRDY }
[65913.727898] ata13.00: failed command: READ FPDMA QUEUED
[65913.728742] ata13.00: cmd 60/00:78:00:80:e3/04:00:3e:01:00/40 tag 15 ncq dma 524288 in
                        res 40/00:80:00:84:e3/00:00:3e:01:00/40 Emask 0x2 (HSM violation)
[65913.730451] ata13.00: status: { DRDY }
[65913.731310] ata13.00: failed command: READ FPDMA QUEUED
[65913.732165] ata13.00: cmd 60/00:80:00:84:e3/04:00:3e:01:00/40 tag 16 ncq dma 524288 in
                        res 40/00:80:00:84:e3/00:00:3e:01:00/40 Emask 0x2 (HSM violation)
[65913.733884] ata13.00: status: { DRDY }
[65913.734741] ata13.00: failed command: READ FPDMA QUEUED
[65913.735599] ata13.00: cmd 60/00:88:00:88:e3/04:00:3e:01:00/40 tag 17 ncq dma 524288 in
                        res 40/00:80:00:84:e3/00:00:3e:01:00/40 Emask 0x2 (HSM violation)
[65913.737319] ata13.00: status: { DRDY }
[65913.738176] ata13.00: failed command: READ FPDMA QUEUED
[65913.739033] ata13.00: cmd 60/00:90:00:8c:e3/04:00:3e:01:00/40 tag 18 ncq dma 524288 in
                        res 40/00:80:00:84:e3/00:00:3e:01:00/40 Emask 0x2 (HSM violation)
[65913.740751] ata13.00: status: { DRDY }
[65913.741609] ata13.00: failed command: READ FPDMA QUEUED
[65913.742464] ata13.00: cmd 60/00:98:00:90:e3/04:00:3e:01:00/40 tag 19 ncq dma 524288 in
                        res 40/00:80:00:84:e3/00:00:3e:01:00/40 Emask 0x2 (HSM violation)
[65913.744189] ata13.00: status: { DRDY }
[65913.745048] ata13.00: failed command: READ FPDMA QUEUED
[65913.745903] ata13.00: cmd 60/00:a0:00:94:e3/04:00:3e:01:00/40 tag 20 ncq dma 524288 in
                        res 40/00:80:00:84:e3/00:00:3e:01:00/40 Emask 0x2 (HSM violation)
[65913.747625] ata13.00: status: { DRDY }
[65913.748500] ata13.00: failed command: READ FPDMA QUEUED
[65913.749356] ata13.00: cmd 60/00:a8:00:98:e3/04:00:3e:01:00/40 tag 21 ncq dma 524288 in
                        res 40/00:80:00:84:e3/00:00:3e:01:00/40 Emask 0x2 (HSM violation)
[65913.751078] ata13.00: status: { DRDY }
[65913.751939] ata13.00: failed command: READ FPDMA QUEUED
[65913.752794] ata13.00: cmd 60/00:b0:00:9c:e3/04:00:3e:01:00/40 tag 22 ncq dma 524288 in
                        res 40/00:80:00:84:e3/00:00:3e:01:00/40 Emask 0x2 (HSM violation)
[65913.754514] ata13.00: status: { DRDY }
[65913.755374] ata13.00: failed command: READ FPDMA QUEUED
[65913.756229] ata13.00: cmd 60/00:b8:00:a0:e3/04:00:3e:01:00/40 tag 23 ncq dma 524288 in
                        res 40/00:80:00:84:e3/00:00:3e:01:00/40 Emask 0x2 (HSM violation)
[65913.757948] ata13.00: status: { DRDY }
[65913.758805] ata13.00: failed command: READ FPDMA QUEUED
[65913.759662] ata13.00: cmd 60/00:c0:00:a4:e3/04:00:3e:01:00/40 tag 24 ncq dma 524288 in
                        res 40/00:80:00:84:e3/00:00:3e:01:00/40 Emask 0x2 (HSM violation)
[65913.761383] ata13.00: status: { DRDY }
[65913.762240] ata13.00: failed command: READ FPDMA QUEUED
[65913.763097] ata13.00: cmd 60/00:c8:00:a8:e3/04:00:3e:01:00/40 tag 25 ncq dma 524288 in
                        res 40/00:80:00:84:e3/00:00:3e:01:00/40 Emask 0x2 (HSM violation)
[65913.764817] ata13.00: status: { DRDY }
[65913.765674] ata13.00: failed command: READ FPDMA QUEUED
[65913.766527] ata13.00: cmd 60/00:d0:00:ac:e3/04:00:3e:01:00/40 tag 26 ncq dma 524288 in
                        res 40/00:80:00:84:e3/00:00:3e:01:00/40 Emask 0x2 (HSM violation)
[65913.768250] ata13.00: status: { DRDY }
[65913.769107] ata13.00: failed command: READ FPDMA QUEUED
[65913.769961] ata13.00: cmd 60/00:d8:00:b0:e3/04:00:3e:01:00/40 tag 27 ncq dma 524288 in
                        res 40/00:80:00:84:e3/00:00:3e:01:00/40 Emask 0x2 (HSM violation)
[65913.771684] ata13.00: status: { DRDY }
[65913.772542] ata13.00: failed command: READ FPDMA QUEUED
[65913.773397] ata13.00: cmd 60/00:e0:00:b4:e3/04:00:3e:01:00/40 tag 28 ncq dma 524288 in
                        res 40/00:80:00:84:e3/00:00:3e:01:00/40 Emask 0x2 (HSM violation)
[65913.775120] ata13.00: status: { DRDY }
[65913.775978] ata13.00: failed command: READ FPDMA QUEUED
[65913.776831] ata13.00: cmd 60/00:e8:00:b8:e3/04:00:3e:01:00/40 tag 29 ncq dma 524288 in
                        res 40/00:80:00:84:e3/00:00:3e:01:00/40 Emask 0x2 (HSM violation)
[65913.778550] ata13.00: status: { DRDY }
[65913.779409] ata13.00: failed command: READ FPDMA QUEUED
[65913.780263] ata13.00: cmd 60/00:f0:00:bc:e3/04:00:3e:01:00/40 tag 30 ncq dma 524288 in
                        res 40/00:80:00:84:e3/00:00:3e:01:00/40 Emask 0x2 (HSM violation)
[65913.781982] ata13.00: status: { DRDY }
[65913.782843] ata13.00: failed command: READ FPDMA QUEUED
[65913.783699] ata13.00: cmd 60/00:f8:00:fc:e3/04:00:3e:01:00/40 tag 31 ncq dma 524288 in
                        res 40/00:80:00:84:e3/00:00:3e:01:00/40 Emask 0x2 (HSM violation)
[65913.785418] ata13.00: status: { DRDY }
[65913.786278] ata13: hard resetting link
[65914.262868] ata13: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[65914.265165] ata13.00: configured for UDMA/133
[65914.265274] ata13: EH complete
[72470.640832] perf: interrupt took too long (2502 > 2500), lowering kernel.perf_event_max_sample_rate to 79750
```

---

### Post by TheFu on 2023-01-02
When looking at logs, it is good to use a tool with proper timestamps, so you can easily tell if those messages are current or from last week. journalctl will do that.

Whenever there are disk issues, you'll want to run a SMART test, give it time to finish, then run a SMART report for each drive.  In the reports for each drive, look for the RAW values and look up those with non-zero numbers, then google what the specific parameter means.  Powered On Hours will always be non-zero.  But if Pending Relocated Sectors/Blocks is non-zero, then you have data loss already.

Drive controllers fail all the time. Sometimes they fail in 1 small way and only communications errors are happening.  This can cause bogus data to be written. Most file systems don't actually validate that the data sent to the drive actually was written accurately.  The only file system I know which does is ZFS.

Communications errors can also be a lose cable or failing cable or interference with the bits on the data cable. Typically, I try re-seating the cables, see if that makes the problems go away. If not, I'll replace the specific cable with the problem.  If that doesn't work, I'll swap the SATA port used on the disk controller/motherboard and see if the error follows the swap or not.  If it does, that's good news - something from the cable to the drive is bad and needs replacement.  Typically, that means a new HDD.

Always ensure you have excellent backups which can handle corrupted files.  This means 1 copy isn't a backup. We really want daily, versioned, backups, so we can have multiple chances to uncover and restore corrupted files before it is too late.

You probably already know this, but RAID is never a backup.  RAID solves 2 issues and only 2 issues.  Data corruption is NOT one.  Versioned backups solve 101+ issues, including a bad RAID.

---

### Post by pqwoerituytrueiwoq on 2023-01-02
All those messages in my post are from today, i had some com errors the day before and and my drive LEDs are not synced like normal, i shutdown the server, made a attempt at fixing the connection, powered it back up and there were no errors, i had this kind of error before i made the array and got it fixed for over a month

this is a software raid 10 array, used ext4 cause i could not figure out how to make it zfs... and i wanted it up and running so ext4 it was

i have at least 2 copies of all data (the entire array counts as 1/2 of that)

i will have a 3ed... how about i get that synced up...

where i see  (This is AFTER the com error i had and a reboot)
```
[63854.882728] md: data-check of RAID array md2
```
i figure it was checking for problems and it found issues caused by the com error i had earlier
then there was a pile of errors
later i see these lines
```
[65044.172995] ata10: EH complete
```
```
[65914.265274] ata13: EH complete
```

does that mean it found errors and was able to fix them?

---

