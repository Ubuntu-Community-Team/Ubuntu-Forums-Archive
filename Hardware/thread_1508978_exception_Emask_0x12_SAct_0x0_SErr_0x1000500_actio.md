---
title: "exception Emask 0x12 SAct 0x0 SErr 0x1000500 action 0x6"
date: 2010-06-13
forum: Hardware
---

### Post by SmplyUnprdctble on 2010-06-13
I have a Dell OptiPlex GX270 with a PCI SATA card in it.  There are three hard drives, a 60GB DeskStar IDE, a 250GB Western Digital IDE, and a 1.5TB Western Digital SATA.

I'm running Lucid with all updates as of posting.

I have my drives partitioned off below:
```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1              2403420    345680   1935648  16% /
/dev/sdc1            240362656 227962440    190416 100% /home
[COLOR=Red] /dev/sdb1            1442145212 780973924 587914488  58% /home/movies[/COLOR]
/dev/sda5              2403420     69204   2212124   4% /tmp
/dev/sda7             49493704   2069852  44909684   5% /usr
/dev/sda6              2403420    502028   1779300  23% /var
```/dev/sdb is the SATA drive in question.  Every time I copy a file from it (**cp /home/media/movie.mpg .**), I get the following message filling up my syslog:

```
Jun 13 15:43:14 Capybara kernel: [   68.618084] ata5.00: exception Emask 0x12 SAct 0x0 SErr 0x1000500 action 0x6
Jun 13 15:43:14 Capybara kernel: [   68.618091] ata5.00: BMDMA stat 0x5
Jun 13 15:43:14 Capybara kernel: [   68.618096] ata5: SError: { UnrecovData Proto TrStaTrns }
Jun 13 15:43:14 Capybara kernel: [   68.618101] ata5.00: failed command: READ DMA
Jun 13 15:43:14 Capybara kernel: [   68.618108] ata5.00: cmd c8/00:00:bf:13:41/00:00:00:00:00/e0 tag 0 dma 131072 in
Jun 13 15:43:14 Capybara kernel: [   68.618110]          res 51/84:bf:bf:13:41/00:00:00:00:00/e0 Emask 0x12 (ATA bus error)
Jun 13 15:43:14 Capybara kernel: [   68.618114] ata5.00: status: { DRDY ERR }
Jun 13 15:43:14 Capybara kernel: [   68.618116] ata5.00: error: { ICRC ABRT }
Jun 13 15:43:14 Capybara kernel: [   68.618127] ata5: hard resetting link
Jun 13 15:43:15 Capybara kernel: [   68.936050] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Jun 13 15:43:15 Capybara kernel: [   68.952943] ata5.00: configured for UDMA/133
Jun 13 15:43:15 Capybara kernel: [   68.952954] ata5: EH complete

```It continues until it gets re-configured for "UDMA/33", and continues to fill the log.

I do not appear to be losing data because of this, but it does take what I would imagine is "way too long" to copy files involving this drive.

The hard drive is brand new, as is the SATA card (I've tried a few SATA cards even).  I found various posts suggesting maybe not enough power in the box, so I bought a bigger power supply with no avail.

Does anyone have an idea how I may resolve this?  I'd be greatly appreciative.  I have attached syslog & dmesg to hopefully help out and can provide additional information as requested.  The attached syslog involves a boot and immediately copying a 79,234,456 byte file from /home/movies (aka /dev/sdb1) to /home/user (aka within /dev/sdc1).

```
$ sudo hdparm -tT /dev/sdb1

/dev/sdb1:
 Timing cached reads:   1902 MB in  2.00 seconds = 951.17 MB/sec
 Timing buffered disk reads:   52 MB in  3.01 seconds =  17.25 MB/sec
```

---

