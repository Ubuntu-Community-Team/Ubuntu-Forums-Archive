---
title: "Sata 2 SSD sata_nv maximum read speed"
date: 2008-10-10
forum: General Help
---

### Post by thegner on 2008-10-10
Hello Everyone!

I have recently obtained a few of those new OCZ v2 SSDs which I must say are very impressive so far.

I am having a slight issue which I was hoping someone could help me diagnose. The drive manufacturer says that it is capable of about 175 MB/s read speeds, but I seem to have hit some kind of ceiling with either my BIOS, ubuntu, or sata_nv. I have 5 of these drives striped with mdadm, but I can still test each drive's read speed individually.

MB: eVGA 680i SLI
OS: Ubuntu 8.04 (fully updated)

```

thegner@it-thegner:~$ uname -a
Linux it-thegner 2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64 GNU/Linux

```

The problem I'm having is that I can't seem to get any single drive read speeds above 133 MB/s (as if that isn't fast enough). Even when I boot into a live cd mode so the disks are guaranteed to be completely idle, it seems to max out on each of 5 drives at 133 MB/s. My dmesg for a typical drive looks like this:

```

thegner@it-thegner:~$ dmesg | grep ata2
[    0.000000] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 10
[    0.000000] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    0.000000] ata2.00: ATA-8: OCZ CORE_SSD, 02.10104, max UDMA/100
[    0.000000] ata2.00: 250445824 sectors, multi 0: LBA 
[    0.000000] ata2.00: configured for UDMA/100

```

And my hdparm -i:

```

thegner@it-thegner:~$ sudo hdparm -i /dev/sda

/dev/sda:

 Model=OCZ CORE_SSD                            , FwRev=02.10104, SerialNo=DC2850809090001C    
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=63
 BuffType=unknown, BuffSize=0kB, MaxMultSect=1, MultSect=?1?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=250445824
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=no WriteCache=disabled
 Drive conforms to: unknown:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode

```

Notice that only udma5 is available and is the "current" mode, but I still can get 133 MB/s, and I thought udma5 was only 100.

hdparm -t --direct:
```

thegner@it-thegner:~$ sudo hdparm -t --direct /dev/sda

/dev/sda:
 Timing O_DIRECT disk reads:  400 MB in  3.00 seconds = 133.19 MB/sec

```

In my troubleshooting I have blacklisted all other libata modules (ata_generic, pata_acpi, etc.) in order to eliminate the possibility that the drives were being loaded with the wrong driver or something.

My BIOS has the IDE controller completely disabled, and as far as I can tell, I'm not using any IDE emulation with the sata connections, but I could be wrong, perhaps that is all my motherboard is capable of.

Typically, this wouldn't be a problem for most people because it's rare that any drive can truly move data at those speeds, but with the advent of Solid State Disks, we need to make sure that ubuntu is capable of delivering the full speed that the sata2 spec is designed for.

I am happy to provide any information needed for further diagnosis.

Does anyone have any configuration suggestions I can try?

Thanks,

Travis

---

### Post by lowflyerUK on 2008-11-22
Dear Travis,

Did you get any more information about SSD speeds?  I have just got the same disk and have exactly the same hdparm results as you but I am using OpenSuse 11.0.

All the best,

Andy

---

### Post by thegner on 2008-11-24
No new news yet. Although I can confirm that the problem still exists in Ubuntu 8.10.

---

### Post by ckeven66 on 2008-11-28
I used Renice brand 64GB SATA SSD, the speed is very satisfied

---

