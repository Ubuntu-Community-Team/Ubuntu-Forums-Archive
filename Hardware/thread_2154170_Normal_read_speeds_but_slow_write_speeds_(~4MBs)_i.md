---
title: "Normal read speeds but slow write speeds (~4MB/s) in 13.04."
date: 2013-06-13
forum: Hardware
---

### Post by ddawsonn on 2013-06-13
I'm seeing very slow write speeds to one of my hard drives in my computer. When I benchmarked the drive in Disks it says Av. read = 140MB/s and Av. write = 4MB/s. The computer is a HP Proliant Microserver n54L. The drive was taken from a 2TB Seagate Expansion external hard drive and is just used for data storage, the OS is on another drive. I don't think it's a problem with the hard drive because when I briefly used it as an external I never noticed any slow write speeds. The drive formatted in Ext3. Can anybody help me out with this, I'm new to Linux in general so I'm not 100% sure that it isn't something I've inadvertently done myself?

---

### Post by ddawsonn on 2013-06-14
bump

---

### Post by matt_symes on 2013-06-14
Hi

Check the output of syslog while writing data to the disk and also search syslog for references to the disk.

Does it provide any clues ?

Kind regards

---

### Post by ddawsonn on 2013-06-14
This is the output of the syslog, are the invalid CHS sectors a sign of the drive failing?

```

Microserver udisksd[1652]: Mounted /dev/sdc1 at /media/microserver/MEDIA on behalf of uid 1000
Jun 14 10:10:57 Microserver kernel: [ 3553.841668] ata3.00: exception Emask 0x0 SAct 0x7fffffff SErr 0x0 action 0x6 frozen
Jun 14 10:10:57 Microserver kernel: [ 3553.841683] ata3.00: failed command: WRITE FPDMA QUEUED
Jun 14 10:10:57 Microserver kernel: [ 3553.841699] ata3.00: cmd 61/00:00:88:f6:16/04:00:00:00:00/40 tag 0 ncq 524288 out
Jun 14 10:10:57 Microserver kernel: [ 3553.841699]          res 40/00:ff:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jun 14 10:10:57 Microserver kernel: [ 3553.841707] ata3.00: status: { DRDY }
Jun 14 10:10:57 Microserver kernel: [ 3553.841713] ata3.00: failed command: WRITE FPDMA QUEUED
Jun 14 10:10:57 Microserver kernel: [ 3553.841726] ata3.00: cmd 61/00:08:88:fa:16/04:00:00:00:00/40 tag 1 ncq 524288 out
Jun 14 10:10:57 Microserver kernel: [ 3553.841726]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jun 14 10:10:57 Microserver kernel: [ 3553.841732] ata3.00: status: { DRDY }
Jun 14 10:10:57 Microserver kernel: [ 3553.841738] ata3.00: failed command: WRITE FPDMA QUEUED
Jun 14 10:10:57 Microserver kernel: [ 3553.841749] ata3.00: cmd 61/88:10:88:fe:16/02:00:00:00:00/40 tag 2 ncq 331776 out
Jun 14 10:10:57 Microserver kernel: [ 3553.841749]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jun 14 10:10:57 Microserver kernel: [ 3553.841755] ata3.00: status: { DRDY }
Jun 14 10:10:57 Microserver kernel: [ 3553.841760] ata3.00: failed command: WRITE FPDMA QUEUED
Jun 14 10:10:57 Microserver kernel: [ 3553.841771] ata3.00: cmd 61/00:18:18:01:17/04:00:00:00:00/40 tag 3 ncq 524288 out
Jun 14 10:10:57 Microserver kernel: [ 3553.841771]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jun 14 10:10:57 Microserver kernel: [ 3553.841777] ata3.00: status: { DRDY }
Jun 14 10:10:57 Microserver kernel: [ 3553.841782] ata3.00: failed command: WRITE FPDMA QUEUED
Jun 14 10:10:57 Microserver kernel: [ 3553.841793] ata3.00: cmd 61/00:20:18:05:17/04:00:00:00:00/40 tag 4 ncq 524288 out
Jun 14 10:10:57 Microserver kernel: [ 3553.841793]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jun 14 10:10:57 Microserver kernel: [ 3553.841799] ata3.00: status: { DRDY }
Jun 14 10:10:57 Microserver kernel: [ 3553.841804] ata3.00: failed command: WRITE FPDMA QUEUED
Jun 14 10:10:57 Microserver kernel: [ 3553.841815] ata3.00: cmd 61/00:28:18:09:17/04:00:00:00:00/40 tag 5 ncq 524288 out
Jun 14 10:10:57 Microserver kernel: [ 3553.841815]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jun 14 10:10:57 Microserver kernel: [ 3553.841821] ata3.00: status: { DRDY }
Jun 14 10:10:57 Microserver kernel: [ 3553.841826] ata3.00: failed command: WRITE FPDMA QUEUED
Jun 14 10:10:57 Microserver kernel: [ 3553.841837] ata3.00: cmd 61/00:30:18:0d:17/04:00:00:00:00/40 tag 6 ncq 524288 out
Jun 14 10:10:57 Microserver kernel: [ 3553.841837]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jun 14 10:10:57 Microserver kernel: [ 3553.841843] ata3.00: status: { DRDY }
Jun 14 10:10:57 Microserver kernel: [ 3553.841848] ata3.00: failed command: WRITE FPDMA QUEUED
Jun 14 10:10:57 Microserver kernel: [ 3553.841860] ata3.00: cmd 61/00:38:18:11:17/04:00:00:00:00/40 tag 7 ncq 524288 out
Jun 14 10:10:57 Microserver kernel: [ 3553.841860]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jun 14 10:10:57 Microserver kernel: [ 3553.841865] ata3.00: status: { DRDY }
Jun 14 10:10:57 Microserver kernel: [ 3553.841870] ata3.00: failed command: WRITE FPDMA QUEUED
Jun 14 10:10:57 Microserver kernel: [ 3553.841882] ata3.00: cmd 61/00:40:18:15:17/04:00:00:00:00/40 tag 8 ncq 524288 out
Jun 14 10:10:57 Microserver kernel: [ 3553.841882]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jun 14 10:10:57 Microserver kernel: [ 3553.841888] ata3.00: status: { DRDY }
Jun 14 10:10:57 Microserver kernel: [ 3553.841893] ata3.00: failed command: WRITE FPDMA QUEUED
Jun 14 10:10:57 Microserver kernel: [ 3553.841904] ata3.00: cmd 61/00:48:18:19:17/04:00:00:00:00/40 tag 9 ncq 524288 out
Jun 14 10:10:57 Microserver kernel: [ 3553.841904]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jun 14 10:10:57 Microserver kernel: [ 3553.841910] ata3.00: status: { DRDY }
Jun 14 10:10:57 Microserver kernel: [ 3553.841915] ata3.00: failed command: WRITE FPDMA QUEUED
Jun 14 10:10:57 Microserver kernel: [ 3553.841926] ata3.00: cmd 61/60:50:18:1d:17/02:00:00:00:00/40 tag 10 ncq 311296 out
Jun 14 10:10:57 Microserver kernel: [ 3553.841926]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jun 14 10:10:57 Microserver kernel: [ 3553.841933] ata3.00: status: { DRDY }
Jun 14 10:10:57 Microserver kernel: [ 3553.841938] ata3.00: failed command: WRITE FPDMA QUEUED
Jun 14 10:10:57 Microserver kernel: [ 3553.841949] ata3.00: cmd 61/08:58:20:c8:12/00:00:06:00:00/40 tag 11 ncq 4096 out
Jun 14 10:10:57 Microserver kernel: [ 3553.841949]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jun 14 10:10:57 Microserver kernel: [ 3553.841955] ata3.00: status: { DRDY }
Jun 14 10:10:57 Microserver kernel: [ 3553.841960] ata3.00: failed command: WRITE FPDMA QUEUED
Jun 14 10:10:57 Microserver kernel: [ 3553.841971] ata3.00: cmd 61/08:60:c0:c8:12/00:00:06:00:00/40 tag 12 ncq 4096 out
Jun 14 10:10:57 Microserver kernel: [ 3553.841971]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jun 14 10:10:57 Microserver kernel: [ 3553.841977] ata3.00: status: { DRDY }
Jun 14 10:10:57 Microserver kernel: [ 3553.841982] ata3.00: failed command: WRITE FPDMA QUEUED
Jun 14 10:10:57 Microserver kernel: [ 3553.841994] ata3.00: cmd 61/08:68:f8:c1:95/00:00:09:00:00/40 tag 13 ncq 4096 out
Jun 14 10:10:57 Microserver kernel: [ 3553.841994]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jun 14 10:10:57 Microserver kernel: [ 3553.841999] ata3.00: status: { DRDY }
Jun 14 10:10:57 Microserver kernel: [ 3553.842004] ata3.00: failed command: WRITE FPDMA QUEUED
Jun 14 10:10:57 Microserver kernel: [ 3553.842016] ata3.00: cmd 61/08:70:f0:c3:95/00:00:09:00:00/40 tag 14 ncq 4096 out
Jun 14 10:10:57 Microserver kernel: [ 3553.842016]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jun 14 10:10:57 Microserver kernel: [ 3553.842021] ata3.00: status: { DRDY }
Jun 14 10:10:57 Microserver kernel: [ 3553.842026] ata3.00: failed command: WRITE FPDMA QUEUED
Jun 14 10:10:57 Microserver kernel: [ 3553.842037] ata3.00: cmd 61/08:78:48:09:01/00:00:00:00:00/40 tag 15 ncq 4096 out
Jun 14 10:10:57 Microserver kernel: [ 3553.842037]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jun 14 10:10:57 Microserver kernel: [ 3553.842043] ata3.00: status: { DRDY }
Jun 14 10:10:57 Microserver kernel: [ 3553.842048] ata3.00: failed command: WRITE FPDMA QUEUED
Jun 14 10:10:57 Microserver kernel: [ 3553.842059] ata3.00: cmd 61/08:80:40:c9:12/00:00:06:00:00/40 tag 16 ncq 4096 out
Jun 14 10:10:57 Microserver kernel: [ 3553.842059]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jun 14 10:10:57 Microserver kernel: [ 3553.842065] ata3.00: status: { DRDY }
Jun 14 10:10:57 Microserver kernel: [ 3553.842070] ata3.00: failed command: WRITE FPDMA QUEUED
Jun 14 10:10:57 Microserver kernel: [ 3553.842081] ata3.00: cmd 61/08:88:58:cb:12/00:00:06:00:00/40 tag 17 ncq 4096 out
Jun 14 10:10:57 Microserver kernel: [ 3553.842081]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jun 14 10:10:57 Microserver kernel: [ 3553.842087] ata3.00: status: { DRDY }
Jun 14 10:10:57 Microserver kernel: [ 3553.842092] ata3.00: failed command: WRITE FPDMA QUEUED
Jun 14 10:10:57 Microserver kernel: [ 3553.842103] ata3.00: cmd 61/10:90:d8:cc:12/00:00:06:00:00/40 tag 18 ncq 8192 out
Jun 14 10:10:57 Microserver kernel: [ 3553.842103]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jun 14 10:10:57 Microserver kernel: [ 3553.842109] ata3.00: status: { DRDY }
Jun 14 10:10:57 Microserver kernel: [ 3553.842114] ata3.00: failed command: WRITE FPDMA QUEUED
Jun 14 10:10:57 Microserver kernel: [ 3553.842125] ata3.00: cmd 61/08:98:40:cd:12/00:00:06:00:00/40 tag 19 ncq 4096 out
Jun 14 10:10:57 Microserver kernel: [ 3553.842125]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jun 14 10:10:57 Microserver kernel: [ 3553.842131] ata3.00: status: { DRDY }
Jun 14 10:10:57 Microserver kernel: [ 3553.842136] ata3.00: failed command: WRITE FPDMA QUEUED
Jun 14 10:10:57 Microserver kernel: [ 3553.842147] ata3.00: cmd 61/08:a0:e0:d0:12/00:00:06:00:00/40 tag 20 ncq 4096 out
Jun 14 10:10:57 Microserver kernel: [ 3553.842147]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jun 14 10:10:57 Microserver kernel: [ 3553.842153] ata3.00: status: { DRDY }
Jun 14 10:10:57 Microserver kernel: [ 3553.842158] ata3.00: failed command: WRITE FPDMA QUEUED
Jun 14 10:10:57 Microserver kernel: [ 3553.842169] ata3.00: cmd 61/08:a8:08:d1:12/00:00:06:00:00/40 tag 21 ncq 4096 out
Jun 14 10:10:57 Microserver kernel: [ 3553.842169]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jun 14 10:10:57 Microserver kernel: [ 3553.842175] ata3.00: status: { DRDY }
Jun 14 10:10:57 Microserver kernel: [ 3553.842180] ata3.00: failed command: WRITE FPDMA QUEUED
Jun 14 10:10:57 Microserver kernel: [ 3553.842191] ata3.00: cmd 61/08:b0:60:d1:12/00:00:06:00:00/40 tag 22 ncq 4096 out
Jun 14 10:10:57 Microserver kernel: [ 3553.842191]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jun 14 10:10:57 Microserver kernel: [ 3553.842197] ata3.00: status: { DRDY }
Jun 14 10:10:57 Microserver kernel: [ 3553.842202] ata3.00: failed command: WRITE FPDMA QUEUED
Jun 14 10:10:57 Microserver kernel: [ 3553.842213] ata3.00: cmd 61/10:b8:a0:d5:12/00:00:06:00:00/40 tag 23 ncq 8192 out
Jun 14 10:10:57 Microserver kernel: [ 3553.842213]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jun 14 10:10:57 Microserver kernel: [ 3553.842219] ata3.00: status: { DRDY }
Jun 14 10:10:57 Microserver kernel: [ 3553.842224] ata3.00: failed command: WRITE FPDMA QUEUED
Jun 14 10:10:57 Microserver kernel: [ 3553.842235] ata3.00: cmd 61/08:c0:f8:c1:0e/00:00:07:00:00/40 tag 24 ncq 4096 out
Jun 14 10:10:57 Microserver kernel: [ 3553.842235]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jun 14 10:10:57 Microserver kernel: [ 3553.842241] ata3.00: status: { DRDY }
Jun 14 10:10:57 Microserver kernel: [ 3553.842246] ata3.00: failed command: WRITE FPDMA QUEUED
Jun 14 10:10:57 Microserver kernel: [ 3553.842257] ata3.00: cmd 61/08:c8:08:c2:0e/00:00:07:00:00/40 tag 25 ncq 4096 out
Jun 14 10:10:57 Microserver kernel: [ 3553.842257]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jun 14 10:10:57 Microserver kernel: [ 3553.842263] ata3.00: status: { DRDY }
Jun 14 10:10:57 Microserver kernel: [ 3553.842268] ata3.00: failed command: WRITE FPDMA QUEUED
Jun 14 10:10:57 Microserver kernel: [ 3553.842279] ata3.00: cmd 61/08:d0:70:c2:0e/00:00:07:00:00/40 tag 26 ncq 4096 out
Jun 14 10:10:57 Microserver kernel: [ 3553.842279]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jun 14 10:10:57 Microserver kernel: [ 3553.842285] ata3.00: status: { DRDY }
Jun 14 10:10:57 Microserver kernel: [ 3553.842290] ata3.00: failed command: WRITE FPDMA QUEUED
Jun 14 10:10:57 Microserver kernel: [ 3553.842301] ata3.00: cmd 61/08:d8:e0:c2:0e/00:00:07:00:00/40 tag 27 ncq 4096 out
Jun 14 10:10:57 Microserver kernel: [ 3553.842301]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jun 14 10:10:57 Microserver kernel: [ 3553.842307] ata3.00: status: { DRDY }
Jun 14 10:10:57 Microserver kernel: [ 3553.842312] ata3.00: failed command: WRITE FPDMA QUEUED
Jun 14 10:10:57 Microserver kernel: [ 3553.842323] ata3.00: cmd 61/10:e0:18:18:00/00:00:08:00:00/40 tag 28 ncq 8192 out
Jun 14 10:10:57 Microserver kernel: [ 3553.842323]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jun 14 10:10:57 Microserver kernel: [ 3553.842329] ata3.00: status: { DRDY }
Jun 14 10:10:57 Microserver kernel: [ 3553.842334] ata3.00: failed command: WRITE FPDMA QUEUED
Jun 14 10:10:57 Microserver kernel: [ 3553.842345] ata3.00: cmd 61/08:e8:28:18:04/00:00:08:00:00/40 tag 29 ncq 4096 out
Jun 14 10:10:57 Microserver kernel: [ 3553.842345]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jun 14 10:10:57 Microserver kernel: [ 3553.842351] ata3.00: status: { DRDY }
Jun 14 10:10:57 Microserver kernel: [ 3553.842356] ata3.00: failed command: WRITE FPDMA QUEUED
Jun 14 10:10:57 Microserver kernel: [ 3553.842367] ata3.00: cmd 61/08:f0:38:18:0c/00:00:08:00:00/40 tag 30 ncq 4096 out
Jun 14 10:10:57 Microserver kernel: [ 3553.842367]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jun 14 10:10:57 Microserver kernel: [ 3553.842373] ata3.00: status: { DRDY }
Jun 14 10:10:57 Microserver kernel: [ 3553.842381] ata3: hard resetting link
Jun 14 10:10:58 Microserver kernel: [ 3554.333491] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jun 14 10:10:58 Microserver kernel: [ 3554.336087] ata3.00: configured for UDMA/133
Jun 14 10:10:58 Microserver kernel: [ 3554.349466] ata3.00: device reported invalid CHS sector 0
Jun 14 10:10:58 Microserver kernel: [ 3554.349478] ata3.00: device reported invalid CHS sector 0
Jun 14 10:10:58 Microserver kernel: [ 3554.349484] ata3.00: device reported invalid CHS sector 0
Jun 14 10:10:58 Microserver kernel: [ 3554.349489] ata3.00: device reported invalid CHS sector 0
Jun 14 10:10:58 Microserver kernel: [ 3554.349493] ata3.00: device reported invalid CHS sector 0
Jun 14 10:10:58 Microserver kernel: [ 3554.349498] ata3.00: device reported invalid CHS sector 0
Jun 14 10:10:58 Microserver kernel: [ 3554.349502] ata3.00: device reported invalid CHS sector 0
Jun 14 10:10:58 Microserver kernel: [ 3554.349506] ata3.00: device reported invalid CHS sector 0
Jun 14 10:10:58 Microserver kernel: [ 3554.349510] ata3.00: device reported invalid CHS sector 0
Jun 14 10:10:58 Microserver kernel: [ 3554.349515] ata3.00: device reported invalid CHS sector 0
Jun 14 10:10:58 Microserver kernel: [ 3554.349519] ata3.00: device reported invalid CHS sector 0
Jun 14 10:10:58 Microserver kernel: [ 3554.349523] ata3.00: device reported invalid CHS sector 0
Jun 14 10:10:58 Microserver kernel: [ 3554.349527] ata3.00: device reported invalid CHS sector 0
Jun 14 10:10:58 Microserver kernel: [ 3554.349532] ata3.00: device reported invalid CHS sector 0
Jun 14 10:10:58 Microserver kernel: [ 3554.349536] ata3.00: device reported invalid CHS sector 0
Jun 14 10:10:58 Microserver kernel: [ 3554.349540] ata3.00: device reported invalid CHS sector 0
Jun 14 10:10:58 Microserver kernel: [ 3554.349545] ata3.00: device reported invalid CHS sector 0
Jun 14 10:10:58 Microserver kernel: [ 3554.349549] ata3.00: device reported invalid CHS sector 0
Jun 14 10:10:58 Microserver kernel: [ 3554.349554] ata3.00: device reported invalid CHS sector 0
Jun 14 10:10:58 Microserver kernel: [ 3554.349558] ata3.00: device reported invalid CHS sector 0
Jun 14 10:10:58 Microserver kernel: [ 3554.349562] ata3.00: device reported invalid CHS sector 0
Jun 14 10:10:58 Microserver kernel: [ 3554.349567] ata3.00: device reported invalid CHS sector 0
Jun 14 10:10:58 Microserver kernel: [ 3554.349571] ata3.00: device reported invalid CHS sector 0
Jun 14 10:10:58 Microserver kernel: [ 3554.349575] ata3.00: device reported invalid CHS sector 0
Jun 14 10:10:58 Microserver kernel: [ 3554.349579] ata3.00: device reported invalid CHS sector 0
Jun 14 10:10:58 Microserver kernel: [ 3554.349583] ata3.00: device reported invalid CHS sector 0
Jun 14 10:10:58 Microserver kernel: [ 3554.349588] ata3.00: device reported invalid CHS sector 0
Jun 14 10:10:58 Microserver kernel: [ 3554.349592] ata3.00: device reported invalid CHS sector 0
Jun 14 10:10:58 Microserver kernel: [ 3554.349596] ata3.00: device reported invalid CHS sector 0
Jun 14 10:10:58 Microserver kernel: [ 3554.349601] ata3.00: device reported invalid CHS sector 0
Jun 14 10:10:58 Microserver kernel: [ 3554.349605] ata3.00: device reported invalid CHS sector 0
Jun 14 10:10:58 Microserver kernel: [ 3554.349642] ata3: EH complete
Jun 14 10:17:01 Microserver CRON[7836]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
```


Edit: I changed SATA ports and that didn't solve the problem so I put the drive back in the enclosure it came in and writing to it from Ubuntu was back to normal, it must be a problem with the computer not the OS. I'll try posting in an HP forum.

---

### Post by matt_symes on 2013-06-14
Hi

I'm not sure what that error is but, as you have suggested, i would look at hardware issues first.

Kind regards

---

