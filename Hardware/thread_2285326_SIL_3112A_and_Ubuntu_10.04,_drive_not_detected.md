---
title: "SIL 3112A and Ubuntu 10.04, drive not detected"
date: 2015-07-04
forum: Hardware
---

### Post by MacManfirst on 2015-07-04
Hi,

I don't know if I post this at the right place, but I just acquired a SATA + eSATA PCI controller SIL 3112A on eBay to put in a old PIII computer.
I'm using ubuntu 10.04 with kernel version 3.13.0-52-generic.

I think the driver is correctly loaded, but the hard drive is never detected, in eSATA or on the internal SATA.
It's a RAID card, but I don't want to use the raid function for now, i just want the drive to be accessible directly.

In dmesg i have: 

[FONT=Andale Mono]```
[    0.000000] BIOS-e820: [mem 0x0000000017fc0000-0x0000000017ff7fff] ACPI data

```[/FONT]```
[FONT=Andale Mono][    0.000000] Memory: 357832K/392568K available (6553K kernel code, 641K rwdata, 2768K rodata, 880K init, 924K bss, 34736K reserved, 0K highmem)[/FONT]
[FONT=Andale Mono][    0.000000]       .data : 0xc1666874 - 0xc19bc600   (3415 kB)[/FONT]
[FONT=Andale Mono][    0.144047] libata version 3.00 loaded.[/FONT]
[FONT=Andale Mono][    2.026571] ata_piix 0000:00:1f.1: version 2.13[/FONT]
[FONT=Andale Mono][    2.030242] scsi0 : ata_piix[/FONT]
[FONT=Andale Mono][    2.030513] scsi1 : ata_piix[/FONT]
[FONT=Andale Mono][    2.030649] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14[/FONT]
[FONT=Andale Mono][    2.030659] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15[/FONT]
[FONT=Andale Mono][    2.305196] ata2.00: ATAPI: PIONEER DVD-RW  DVR-110, 1.37, max UDMA/66[/FONT]
[FONT=Andale Mono][    2.305217] ata2.00: limited to UDMA/33 due to 40-wire cable[/FONT]
[FONT=Andale Mono][    2.306712] ata1.00: ATA-7: Maxtor 6L080P0, BAJ41G20, max UDMA/133[/FONT]
[FONT=Andale Mono][    2.306726] ata1.00: 160086528 sectors, multi 16: LBA48 [/FONT]
[FONT=Andale Mono][    2.320485] ata2.00: configured for UDMA/33[/FONT]
[FONT=Andale Mono][    2.322146] ata1.00: configured for UDMA/100[/FONT]
[FONT=Andale Mono][    2.391195] Write protecting the kernel read-only data: 2772k[/FONT]
[FONT=Andale Mono][    2.709785] sata_sil 0000:01:0d.0: version 2.4[/FONT]
[FONT=Andale Mono][    2.735612] scsi2 : sata_sil[/FONT]
[FONT=Andale Mono][    2.748971] scsi3 : sata_sil[/FONT]
[FONT=Andale Mono][    2.749162] ata3: SATA max UDMA/100 mmio m512@0xff8ffc00 tf 0xff8ffc80 irq 9[/FONT]
[FONT=Andale Mono][    2.749173] ata4: SATA max UDMA/100 mmio m512@0xff8ffc00 tf 0xff8ffcc0 irq 9[/FONT]
[FONT=Andale Mono][    3.068222] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)[/FONT]
[FONT=Andale Mono][    3.521192] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)[/FONT]
[FONT=Andale Mono][    3.524208] ata3.00: NODEV after polling detection[/FONT]
[FONT=Andale Mono][    3.844071] ata4: SATA link down (SStatus 0 SControl 310)[/FONT]
[FONT=Andale Mono][   11.839287] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[/FONT]
```
[FONT=Andale Mono]
[/FONT]The sda1 and sda2 is the internal IDE drive. 
The line *[FONT=Andale Mono]NODEV after polling detection [/FONT]*is weird, what does it means ?

Here's the lspci -v output:
```

[FONT=Andale Mono]01:0d.0 RAID bus controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 01)[/FONT]
[FONT=Andale Mono]    Subsystem: Silicon Image, Inc. SiI 3112 SATARaid Controller[/FONT]
[FONT=Andale Mono]    Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 9[/FONT]
[FONT=Andale Mono]    I/O ports at cff0 [size=8][/FONT]
[FONT=Andale Mono]    I/O ports at cfe4 [size=4][/FONT]
[FONT=Andale Mono]    I/O ports at cfa8 [size=8][/FONT]
[FONT=Andale Mono]    I/O ports at cfe0 [size=4][/FONT]
[FONT=Andale Mono]    I/O ports at cf90 [size=16][/FONT]
[FONT=Andale Mono]    Memory at ff8ffc00 (32-bit, non-prefetchable) [size=512][/FONT]
[FONT=Andale Mono]    Expansion ROM at ff800000 [disabled] [size=512K][/FONT]
[FONT=Andale Mono]    Capabilities: [60] Power Management version 2[/FONT]
[FONT=Andale Mono]Kernel driver in use: sata_sil[/FONT]

```

Finally the lsmod command:

[FONT=Andale Mono]```

Module                  Size  Used by
```[/FONT]```
 [FONT=Andale Mono]cfg80211              409394  0 [/FONT]
[FONT=Andale Mono]gpio_ich               13229  0 [/FONT]
[FONT=Andale Mono]ppdev                  17391  0 [/FONT]
[FONT=Andale Mono]snd_wavefront          38120  0 [/FONT]
[FONT=Andale Mono]radeon               1420720  1 [/FONT]
[FONT=Andale Mono]snd_cs4236             29167  0 [/FONT]
[FONT=Andale Mono]snd_intel8x0           33110  0 [/FONT]
[FONT=Andale Mono]snd_ac97_codec        105709  1 snd_intel8x0[/FONT]
[FONT=Andale Mono]snd_opl3_lib           18651  2 snd_wavefront,snd_cs4236[/FONT]
[FONT=Andale Mono]ac97_bus               12642  1 snd_ac97_codec[/FONT]
[FONT=Andale Mono]snd_hwdep              13272  2 snd_wavefront,snd_opl3_lib[/FONT]
[FONT=Andale Mono]snd_wss_lib            29835  2 snd_wavefront,snd_cs4236[/FONT]
[FONT=Andale Mono]ttm                    80983  1 radeon[/FONT]
[FONT=Andale Mono]snd_pcm                85501  4 snd_ac97_codec,snd_intel8x0,snd_wss_lib,snd_cs4236[/FONT]
[FONT=Andale Mono]drm_kms_helper         48868  1 radeon[/FONT]
[FONT=Andale Mono]serio_raw              13230  0 [/FONT]
[FONT=Andale Mono]snd_page_alloc         14230  3 snd_intel8x0,snd_wss_lib,snd_pcm[/FONT]
[FONT=Andale Mono]ns558                  12586  0 [/FONT]
[FONT=Andale Mono]snd_mpu401             13724  0 [/FONT]
[FONT=Andale Mono]drm                   244037  3 ttm,drm_kms_helper,radeon[/FONT]
[FONT=Andale Mono]snd_timer              28584  3 snd_wss_lib,snd_pcm,snd_opl3_lib[/FONT]
[FONT=Andale Mono]snd_mpu401_uart        13865  3 snd_wavefront,snd_cs4236,snd_mpu401[/FONT]
[FONT=Andale Mono]i2c_algo_bit           13197  1 radeon[/FONT]
[FONT=Andale Mono]snd_rawmidi            25135  2 snd_wavefront,snd_mpu401_uart[/FONT]
[FONT=Andale Mono]gameport               15189  2 ns558[/FONT]
[FONT=Andale Mono]snd_seq_device         14137  2 snd_rawmidi,snd_opl3_lib[/FONT]
[FONT=Andale Mono]lpc_ich                16864  0 [/FONT]
[FONT=Andale Mono]snd                    60939  13 snd_ac97_codec,snd_intel8x0,snd_hwdep,snd_timer,snd_wss_lib,snd_pcm,snd_rawmidi,snd_wavefront,snd_mpu401_uart,snd_seq_device,snd_cs4236,snd_opl3_lib,snd_mpu401[/FONT]
[FONT=Andale Mono]soundcore              12600  1 snd[/FONT]
[FONT=Andale Mono]parport_pc             31981  1 [/FONT]
[FONT=Andale Mono]shpchp                 32128  0 [/FONT]
[FONT=Andale Mono]mac_hid                13037  0 [/FONT]
[FONT=Andale Mono]lp                     13299  0 [/FONT]
[FONT=Andale Mono]parport                40836  3 lp,ppdev,parport_pc[/FONT]
[FONT=Andale Mono]skge                   44279  0 [/FONT]
[FONT=Andale Mono]pata_acpi              12886  0 [/FONT]
[FONT=Andale Mono]psmouse                91357  0 [/FONT]
[FONT=Andale Mono]e100                   35945  0 [/FONT]
[FONT=Andale Mono]floppy                 55416  0 [/FONT]
[FONT=Andale Mono]mii                    13654  1 e100[/FONT]
[FONT=Andale Mono]sata_sil               13256  0 [/FONT]

```

But, if I plug the drive in usb, it detects it, and the drive have no problem the be mounted. (only it's usb 1.1 :D )

Any advice on how to get this work ? 

Thank you!

---

### Post by Yellow Pasque on 2015-07-04
What model hard disk and SATA card?

---

### Post by MacManfirst on 2015-07-04
The SATA card is this one :[ ]("http://r.ebay.com/8PyEEY")[COLOR=#000000][FONT=Helvetica][http://r.ebay.com/8PyEEY](http://r.ebay.com/8PyEEY)
The hard drive is Western Digital caviar green 2 TB : WD20EARS.[/FONT][/COLOR]

---

### Post by weatherman2 on 2015-07-04
As I recall, there's a BIOS setup of some sort just for the RAID card - can you access it?  I have a card similar to that one, and after POST it briefly shows what drives are connected to it, before the OS boots.  Do you see anything like that?  Can you go in to the setup and try to configure the card's settings?  (Forget what key it would be - I think it told me on the screen.)

---

### Post by MacManfirst on 2015-07-04
> **weatherman2 said:**
> As I recall, there's a BIOS setup of some sort just for the RAID card - can you access it?  I have a card similar to that one, and after POST it briefly shows what drives are connected to it, before the OS boots.  Do you see anything like that?  Can you go in to the setup and try to configure the card's settings?  (Forget what key it would be - I think it told me on the screen.)

Yes, I see the "raid" card message at boot, and the drive is correctly showed with the capacity of 1863 GB.

Inside the "RAID configuration Utility" i see the drive: 0 PM WDC WD20EARS-... 1863 GB

Now in dmesg there're new interesting "lines":
```

ata3:00 qc timeout (cmd 0xec)
ata3:00 failed to IDENTIFY (I/O error, err_mask=0x5)

```

---

### Post by Bucky Ball on 2015-07-04
Just a note: 10.04 LTS is EOL. No doubt your issues will continue to multiply as time goes by. I advise you upgrade to a supported release, probably 14.04 LTS would suit you, supported until 2019.

End-of-life unsupported releases are not officially supported here. Please read these. Good luck. 

EOL release recommendations:
[http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730)

EOL link:
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

UPGRADE notes:
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

### Post by Yellow Pasque on 2015-07-04
Try forcing SATA 1.5 Gb/s mode on the drive: [http://wdc.custhelp.com/app/answers/detail/search/1/a_id/1679#jumper](http://wdc.custhelp.com/app/answers/detail/search/1/a_id/1679#jumper)
You could also try another SATA cable to rule that out...

---

