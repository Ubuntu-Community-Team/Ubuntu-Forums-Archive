---
title: "Hard disk DMA Mode isn't working (using PIO)"
date: 2010-02-03
forum: Hardware
---

### Post by shebangs on 2010-02-03
Ubuntu Server 8.04.3 - 64bit

Two separate hard disks.   If I put both disks in the following IDE configuration, DMA works on _both disks_ as expected:

IDE0:0:  HARD_DISK_20GB
IDE0:1:  HARD_DISK_40GB
IDE1:0:  empty
IDE1:1:  empty

However, if I change it to the below config, it doesn't work.  Only HARD_DISK_20GB has DMA, HARD_DISK_40GB uses PIO mode.   This is really slow and usable.

IDE0:0:  HARD_DISK_20GB
IDE0:1:  empty
IDE1:0:  HARD_DISK_40GB
IDE1:1:  empty

I have added the following to /etc/modprobe.d/aliases
```
~# cat /etc/modprobe.d/aliases | tail -2
alias ata_generic off
alias pata_atiixp on
~# uname -a
Linux ez-greentrac 2.6.24-24-server #1 SMP Tue Jul 7 19:39:36 UTC 2009 x86_64 GNU/Linux

```

Info below:
```
~# dmesg | grep ata1.0
[   12.135067] ata1.00: ATA-0: Virtual HD, 1.1.0, max MWDMA2
[   12.135072] ata1.00: 41942880 sectors, multi 128: LBA 
[   12.138203] ata1.00: configured for MWDMA2
[   12.142940] ata1.00: configured for MWDMA2
# dmesg | grep ata2.0
[   12.304665] ata2.00: ATA-0: Virtual HD, 1.1.1, max MWDMA2
[   12.304670] ata2.00: 83884800 sectors, multi 128: LBA 
[   12.304678] ata2.00: simplex DMA is claimed by other device, disabling DMA
[   12.307473] ata2.00: configured for PIO4
[   12.309254] ata2.00: simplex DMA is claimed by other device, disabling DMA
[   12.312071] ata2.00: configured for PIO4

```



Any ideas please?  This is really killing our Application.

---

### Post by shebangs on 2010-02-11
Anyone?

Maybe this isnt the correct place to report this?

---

