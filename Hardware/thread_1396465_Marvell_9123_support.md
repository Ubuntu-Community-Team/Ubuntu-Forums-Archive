---
title: "Marvell 9123 support"
date: 2010-02-02
forum: Hardware
---

### Post by derx on 2010-02-02
I'm thinking of buying a pcie sata controller with a Marvell 9123 controller on it, but I can't find if it is supported in ubuntu 8.04.4 LTS, or ubuntu in general. I searched here on the forum, and via Google, but I can't find info about using a marvell 9123 in linux. 
Is there a driver available, and can I use it under 8.04.4 LTS ?

Thanks

---

### Post by sune_cph on 2010-03-31
I have a brand-new ASUS P6X58D-Premium board that has this controller on-board (for SATA 6G support). 

While it appears the Marvell 9123 works fine in Linux (I use Xubuntu 9.10/kernell 2.26.31-20), it invariably hangs up my SSD drive (tested with both a sata 3G/6G ssd) after some random time. I have no issues on the normal Intel ACHI sata 3G ports, only on the Marvell Sata 6G ports.

On the other hand, my dual boot Windows XP works fine (once the Marvel achi driver has been installed) so it's not like the Marvell controller is flaky or anything.

/sune

---

### Post by m4tr1x23 on 2010-07-05
> **sune_cph said:**
> I have a brand-new ASUS P6X58D-Premium board that has this controller on-board (for SATA 6G support). 

While it appears the Marvell 9123 works fine in Linux (I use Xubuntu 9.10/kernell 2.26.31-20), it invariably hangs up my SSD drive (tested with both a sata 3G/6G ssd) after some random time. I have no issues on the normal Intel ACHI sata 3G ports, only on the Marvell Sata 6G ports.

On the other hand, my dual boot Windows XP works fine (once the Marvel achi driver has been installed) so it's not like the Marvell controller is flaky or anything.

/sune

I have same motherboard but marvell 9123 controller don't work very well for me.
With ubuntu-maverick kernel it's work well but when i transfer big files to sata3 hd i see this error on dmesg:

[ 1419.788450] ata7.00: exception Emask 0x10 SAct 0x3 SErr 0x100000 action 0x6 frozen
[ 1419.788455] ata7.00: irq_stat 0x08000000, interface fatal error
[ 1419.788458] ata7: SError: { Dispar }
[ 1419.788462] ata7.00: failed command: READ FPDMA QUEUED
[ 1419.788469] ata7.00: cmd 60/00:00:5c:35:ad/01:00:5e:00:00/40 tag 0 ncq 131072 in
[ 1419.788470]          res 40/00:0c:5c:36:ad/00:00:5e:00:00/40 Emask 0x10 (ATA bus error)
[ 1419.788474] ata7.00: status: { DRDY }
[ 1419.788476] ata7.00: failed command: READ FPDMA QUEUED
[ 1419.788483] ata7.00: cmd 60/00:08:5c:36:ad/01:00:5e:00:00/40 tag 1 ncq 131072 in
[ 1419.788484]          res 40/00:0c:5c:36:ad/00:00:5e:00:00/40 Emask 0x10 (ATA bus error)
[ 1419.788488] ata7.00: status: { DRDY }
[ 1419.788492] ata7: hard resetting link
[ 1420.314232] ata7: SATA link up 6.0 Gbps (SStatus 133 SControl 370)
[ 1420.318838] ata7.00: configured for UDMA/133
[ 1420.318850] ata7: EH complete

You try to connect 2 sata3 disk on this controller ?

Thanks

---

### Post by moojix on 2010-08-06
I had a similar ugly ata errors with my SATA3 drive  Crucial C300 and ASUS P7P55E Premium

```
Aug  6 09:58:08 st-002 kernel: [   34.136510] ata5.00: exception Emask 0x0 SAct 0x3f SErr 0x0 action 0x6 frozen
Aug  6 09:58:08 st-002 kernel: [   34.136571] ata5.00: failed command: READ FPDMA QUEUED
Aug  6 09:58:08 st-002 kernel: [   34.136620] ata5.00: cmd 60/e0:00:28:6d:80/01:00:04:00:00/40 tag 0 ncq 245760 in
Aug  6 09:58:08 st-002 kernel: [   34.136621]          res 40/00:3c:08:53:80/00:00:04:00:00/40 Emask 0x4 (timeout)
Aug  6 09:58:08 st-002 kernel: [   34.136715] ata5.00: status: { DRDY }
...
Aug  6 09:58:08 st-002 kernel: [   34.137835] ata5: hard resetting link
Aug  6 09:58:08 st-002 kernel: [   34.666468] ata5: SATA link up 6.0 Gbps (SStatus 133 SControl 370)
Aug  6 09:58:08 st-002 kernel: [   34.667896] ata5.00: configured for UDMA/100
Aug  6 09:58:08 st-002 kernel: [   34.667904] ata5.00: device reported invalid CHS sector 0
Aug  6 09:58:08 st-002 kernel: [   34.667908] ata5.00: device reported invalid CHS sector 0
Aug  6 09:58:08 st-002 kernel: [   34.667911] ata5.00: device reported invalid CHS sector 0
Aug  6 09:58:08 st-002 kernel: [   34.667914] ata5.00: device reported invalid CHS sector 0
Aug  6 09:58:08 st-002 kernel: [   34.667918] ata5.00: device reported invalid CHS sector 0
Aug  6 09:58:08 st-002 kernel: [   34.667931] ata5: EH complete

```

My solution, was disabling NCQ.
see: [http://ubuntuforums.org/showpost.php?p=9684933&postcount=12](http://ubuntuforums.org/showpost.php?p=9684933&postcount=12)

--
moojix

---

