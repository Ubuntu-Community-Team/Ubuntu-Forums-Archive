---
title: "very slow SATA HDD speed on Gigabyte MB.  Anyone else with a Gigabyte MB?"
date: 2009-12-25
forum: Hardware
---

### Post by graysky on 2009-12-25
I have a Gigabyte EG45M-UD2H mother board (running the latest BIOS called F3).  I'm noticing a pretty significant HDD speed decrease with this board vs. my old board.  If I take the same Seagate 7200.12 (1 TB) HDD and benchmark it on another motherboard, the cached reads are about 7x higher!

For example, under the EG45M-UD2H:
```
$ sudo hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:   2692 MB in  2.00 seconds = 1346.47 MB/sec
 Timing buffered disk reads:  386 MB in  3.01 seconds = 128.13 MB/sec
```
On another motherboard (DFI LP P35-T2R):
```
$ sudo hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:   14740 MB in  2.00 seconds = 7378.19 MB/sec
 Timing buffered disk reads:  368 MB in  3.02 seconds = 122.04 MB/sec
```

**If you're running a Gigabyte motherboard, can you please post the output of the hdparm -Tt /dev/sdxy command?  Also, please post the model number of the motherboard which HDD you have.**

The only relevant settings I see in the BIOS are:

BIOS settings: Integrated Peripherals>SATA RAID/AHCI Mode [AHCI]  <-- I have also set this to disable and there is no difference
SATA Port0-3 Native Mode [Enabled or Disabled] <-- I tried both and there is no difference

Does anyone have any thoughts?

```
$ lsmod | grep ahci
ahci                   34321  4 
libata                151860  4 pata_acpi,ata_generic,ahci,pata_jmicron
```

---

### Post by graysky on 2009-12-27
EDIT: This whole issue is a non-issue -- PEBKAC.  Seems as though I was misusing the -T switch:
[quote="hdparm manpage"]-T

Perform  timings  of  cache reads for benchmark and comparison purposes.  This displays the speed of reading directly from the Linux buffer  cache  without  disk  access. This measurement is essentially an indication of the throughput of the processor, cache, and memory of the system under test.[/quote]

---

