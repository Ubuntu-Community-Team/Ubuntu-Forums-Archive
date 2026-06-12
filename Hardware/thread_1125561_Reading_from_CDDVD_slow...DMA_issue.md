---
title: "Reading from CD/DVD slow...DMA issue?"
date: 2009-04-14
forum: Hardware
---

### Post by ragtag on 2009-04-14
I'm having a problem with reading from my optical IDE drive. It uses all of the CPU when playing DVD's or reading files from it, and the machine becomes slow and jerky. I think it has something to do with DMA settings, but I'm not able to figure it out.

```
>> mount | egrep 'udf|iso9660'
/dev/scd0 on /media/LITTLE_NORSE_PRINCE type udf (ro,nosuid,nodev,uhelper=hal,uid=1000)
```

Which indicates it's an ATAPI device. Then I run:
```

>> dmesg | grep ata5
[    5.987753] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    6.148474] ata5.00: ATAPI: Optiarc DVD RW AD-5200A, 1.05, max UDMA/66
[    6.148487] ata5.00: WARNING: ATAPI DMA disabled for reliablity issues.  It can be enabled
[    6.148489] ata5.00: WARNING: via pata_ali.atapi_dma modparam or corresponding sysfs node.
[    6.164412] ata5.00: configured for UDMA/66

```

It seems it disables the DMA for reliability reasons...and that I can enable it, but I don't understand how.

I tried following the instructions [here]("https://help.ubuntu.com/community/DMA") for the ATAPI drive, but that did nothing. The error they get is also different from mine.

So, any idea how to fix this?

My machine is and AMD64 one, with via chipset, I believe. Finally, here is the complete dmesg | grep ata dump, in case it's helpfull.

```
[    0.004000]       .data : 0xc03843ea - 0xc04a7680   (1164 kB)
[    2.044667] Write protecting the kernel read-only data: 940k
[    3.568085] libata version 3.00 loaded.
[    4.554988] sata_uli 0000:00:1f.1: version 1.3
[    4.555002] sata_uli 0000:00:1f.1: enabling device (0105 -> 0107)
[    4.555010] sata_uli 0000:00:1f.1: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    4.555592] scsi0 : sata_uli
[    4.555886] scsi1 : sata_uli
[    4.556153] scsi2 : sata_uli
[    4.556407] scsi3 : sata_uli
[    4.556446] ata1: SATA max UDMA/133 cmd 0xec00 ctl 0xe880 bmdma 0xe400 irq 21
[    4.556450] ata2: SATA max UDMA/133 cmd 0xe800 ctl 0xe480 bmdma 0xe408 irq 21
[    4.556454] ata3: SATA max UDMA/133 cmd 0xec08 ctl 0xe886 bmdma 0xe410 cmd 0xe809 ctl 0xe486 bmdma 0xe418 irq 21
[    4.556457] ata4: SATA max UDMA/133 irq 21
[    5.024061] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.032438] ata1.00: ATA-7: SAMSUNG HD103UJ, 1AA01112, max UDMA7
[    5.032441] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    5.040440] ata1.00: configured for UDMA/133
[    5.976236] pata_acpi 0000:00:1f.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    5.976283] pata_acpi 0000:00:1f.0: PCI INT A disabled
[    5.980457] pata_ali 0000:00:1f.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    5.980822] scsi4 : pata_ali
[    5.986020] scsi5 : pata_ali
[    5.987753] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    5.987756] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    6.148474] ata5.00: ATAPI: Optiarc DVD RW AD-5200A, 1.05, max UDMA/66
[    6.148487] ata5.00: WARNING: ATAPI DMA disabled for reliablity issues.  It can be enabled
[    6.148489] ata5.00: WARNING: via pata_ali.atapi_dma modparam or corresponding sysfs node.
[    6.164412] ata5.00: configured for UDMA/66
[   15.764186] EXT3-fs: mounted filesystem with ordered data mode.
[   36.951974] EXT3-fs: mounted filesystem with ordered data mode.

```

:confused:

---

### Post by morfeasrev on 2009-04-24
I`m experiencing the same problem in jaunty!!!
```

ata5.00: ATAPI: _NEC DVD_RW ND-3550A, 1.05, max UDMA/33
[    3.156549] ata5.00: WARNING: ATAPI DMA disabled for reliablity issues.  It can be enabled
[    3.156552] ata5.00: WARNING: via pata_ali.atapi_dma modparam or corresponding sysfs node.
[    3.172474] ata5.00: configured for UDMA/33

```

On Intrepid using adding "pata_ali atapi_dma=1" at the end of /etc/initramfs-tools/modules
```
sudo gedit /etc/initramfs-tools/modules
``` and running 
```
sudo update-initramfs -u
```
(as noted here [http://ubuntuforums.org/showthread.php?t=938939]("http://ubuntuforums.org/showpost.php?p=6043504&postcount=8") by psyke83)
did the trick for me.

Hope this helps you.
Unfortunately the above methodology does not work for me on jaunty:confused:

---

### Post by nrune on 2009-04-26
Thanks for this help, it fixed my 8.10 system!  

I guess I should avoid 9.04 for now. 

Mike

---

### Post by rmbell on 2009-05-18
Didn't work for me on jaunty either. help?

---

### Post by ablewisuk on 2009-06-27
> **rmbell said:**
> Didn't work for me on jaunty either. help?

I had the same problem on Ubuntu 9.04 -- DVD playback was skipping with VLC outputting "main video output warning: late picture skipped" warnings, and this message in dmesg:

```
ata5.01: WARNING: ATAPI DMA disabled for reliablity issues.  It can be enabled
ata5.01: WARNING: via pata_ali.atapi_dma modparam or corresponding sysfs node.
```

It was fixed by becoming root and following the advice in the message:

```
$ sudo su
# echo 1 > /sys/module/pata_ali/parameters/atapi_dma
```

---

### Post by morfeasrev on 2010-05-02
I think its fixed for me on 10.04!!!
dmesg | grep ata5 gives me:
```

[    0.817406] ata5: SATA max UDMA/133 cmd 0xd408 ctl 0xd006 bmdma 0xc010 cmd 0xc809 ctl 0xc406 bmdma 0xc018 irq 21

```

I get 2.5MB/sec transfer rates, on coping a file from a DVD (sounds good to me).

---

