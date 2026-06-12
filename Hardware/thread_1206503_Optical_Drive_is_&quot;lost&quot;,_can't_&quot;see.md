---
title: "Optical Drive is &quot;lost&quot;, can't &quot;see&quot; it anywhere"
date: 2009-07-07
forum: Hardware
---

### Post by padrecovsky on 2009-07-07
Hello,

so here's the problem. When I installed Ubuntu a month ago i had my optical drive disconnected (can't remember why i had disconnected it), and installed ubuntu through a pen drive. Everything's been working fine, but yesterday i had the need to copy some things i have backed up on dvds and reconnected the drive. The problem is the drive is working, since i'm able to open it and close it but it doesn't appears anywhere at all.
What should I do to have it working?
I feel i have to point out that i'm a total noob when it comes to Ubuntu.

All help is welcomed.


Cheers

---

### Post by padrecovsky on 2009-07-07
Can someone please lend a hand?
I would really love to have the drive working :smile:

Thanks in advance


Cheers

---

### Post by padrecovsky on 2009-07-08
Doesn't anybody has any suggestion to what i can do?



Cheers

---

### Post by vikkikanhaua on 2009-07-08
in nautilus check the Go --> Computer section if ur drive is listed in there & also try```
dmesg | grep ata
``` to see if ur drive is recognised

---

### Post by padrecovsky on 2009-07-08
```
[    0.000000]  BIOS-e820: 000000007ffc0000 - 000000007ffce000 (ACPI data)
[    0.000000]  modified: 000000007ffc0000 - 000000007ffce000 (ACPI data)
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.004000] Memory: 2052960k/2096896k available (4110k kernel code, 42680k reserved, 2196k data, 532k init, 1191688k highmem)
[    0.004000]       .data : 0xc0503b9f - 0xc0728e60   (2196 kB)
[    0.462443] libata version 3.00 loaded.
[    1.498489] ata_piix 0000:00:1f.1: version 2.12
[    1.498510] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.498567] ata_piix 0000:00:1f.1: setting latency timer to 64
[    1.498702] scsi0 : ata_piix
[    1.498840] scsi1 : ata_piix
[    1.500456] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    1.500460] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    1.672493] ata1.01: ATA-7: SAMSUNG HD300LD, WK100-12, max UDMA/100
[    1.672497] ata1.01: 586072368 sectors, multi 16: LBA48 
[    1.672523] ata1.01: limited to UDMA/33 due to 40-wire cable
[    1.680435] ata1.01: configured for UDMA/33
[    1.888379] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.888384] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    1.888439] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.888551] scsi2 : ata_piix
[    1.888646] scsi3 : ata_piix
[    1.890107] ata3: SATA max UDMA/133 cmd 0xc400 ctl 0xc080 bmdma 0xb880 irq 19
[    1.890111] ata4: SATA max UDMA/133 cmd 0xc000 ctl 0xbc00 bmdma 0xb888 irq 19
[    2.219256] pata_it821x 0000:04:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.219261] pata_it821x: controller in smart mode.
[    2.219302] pata_it821x 0000:04:01.0: setting latency timer to 64
[    2.221514] pata_it821x: Firmware 02/09/3030
[    2.221599] scsi4 : pata_it821x
[    2.221696] scsi5 : pata_it821x
[    2.221744] ata5: PATA max UDMA/133 cmd 0xec00 ctl 0xe880 bmdma 0xe400 irq 17
[    2.221747] ata6: PATA max UDMA/133 cmd 0xe800 ctl 0xe480 bmdma 0xe408 irq 17
[    3.512275] ata5.00: ATA-7: Maxtor 6Y160P0, YAR41BW0, max UDMA/100
[    3.512279] ata5.00: 312581808 sectors, multi 0: LBA48 
[    3.512314] ata5.01: ATA-6: ST3120022A, 3.06, max UDMA/100
[    3.512317] ata5.01: 234441648 sectors, multi 0: LBA48 
[    3.512341] ata5.00: configured for DMA
[    3.512344] ata5.01: configured for DMA
[    3.747901] Write protecting the kernel read-only data: 1524k
[    7.630433] EXT4-fs: mounted filesystem with ordered data mode.

```

Where do i see if it is recognised or not?
Thanks

Cheers

---

### Post by vikkikanhaua on 2009-07-08
are u having an optical drive of samsung or maxtor...

---

### Post by padrecovsky on 2009-07-08
> **vikkikanhaua said:**
> are u having an optical drive of samsung or maxtor...

The optical drive is LG.
Samsung and maxtor are the hard drives.
Sp what does that all means?


Cheers

---

### Post by vikkikanhaua on 2009-07-08
please try to find out ur LG drive in o/p of only dmesg & if it's not there then it might be a problem of hardware coz your kernel is not detecting ur optical drive.
also make sure that all jumpers r properly connected.

btw dmesg gives the output of all hardware related stuff like if u plugin an usb drive then u can check dmesg for it's drive letter

---

### Post by padrecovsky on 2009-07-08
> **vikkikanhaua said:**
> please try to find out ur LG drive in o/p of only dmesg & if it's not there then it might be a problem of hardware coz your kernel is not detecting ur optical drive.
also make sure that all jumpers r properly connected.

btw dmesg gives the output of all hardware related stuff like if u plugin an usb drive then u can check dmesg for it's drive letter

Ok thanks, i'll try and see that and tomorrow i'll post any changes.


Cheers

---

