---
title: "Frequent ATA errors in kernel"
date: 2016-01-22
forum: Hardware
---

### Post by mistcloud-misty on 2016-01-22
Ever since a system crash I had a couple weeks ago I noticed this appearing in my kernel logs 2-4 times a day, every day:

```
Jan 22 10:27:51 arcane-X555LB kernel: [637871.133715] asus_wmi: Unknown key cf pressed
Jan 22 10:27:52 arcane-X555LB kernel: [637871.630477] ata1.00: exception Emask 0x10 SAct 0x0 SErr 0x50000 action 0xe frozen
Jan 22 10:27:52 arcane-X555LB kernel: [637871.630481] ata1.00: irq_stat 0x00400000, PHY RDY changed
Jan 22 10:27:52 arcane-X555LB kernel: [637871.630484] ata1: SError: { PHYRdyChg CommWake }
Jan 22 10:27:52 arcane-X555LB kernel: [637871.630487] ata1.00: failed command: IDENTIFY DEVICE
Jan 22 10:27:52 arcane-X555LB kernel: [637871.630492] ata1.00: cmd ec/00:01:00:00:00/00:00:00:00:00/40 tag 26 pio 512 in
Jan 22 10:27:52 arcane-X555LB kernel: [637871.630492]          res 50/00:00:00:00:00/00:00:00:00:00/00 Emask 0x10 (ATA bus error)
Jan 22 10:27:52 arcane-X555LB kernel: [637871.630494] ata1.00: status: { DRDY }
Jan 22 10:27:52 arcane-X555LB kernel: [637871.630498] ata1: hard resetting link
Jan 22 10:27:52 arcane-X555LB kernel: [637872.352847] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Jan 22 10:27:52 arcane-X555LB kernel: [637872.355583] ata1.00: configured for UDMA/133
Jan 22 10:27:53 arcane-X555LB kernel: [637872.368848] ata1: EH complete
Jan 22 10:27:53 arcane-X555LB kernel: [637872.444858] ata2.00: exception Emask 0x10 SAct 0x0 SErr 0x50000 action 0xe frozen
Jan 22 10:27:53 arcane-X555LB kernel: [637872.444862] ata2.00: irq_stat 0x00400000, PHY RDY changed
Jan 22 10:27:53 arcane-X555LB kernel: [637872.444864] ata2: SError: { PHYRdyChg CommWake }
Jan 22 10:27:53 arcane-X555LB kernel: [637872.444868] sr 1:0:0:0: CDB: 
Jan 22 10:27:53 arcane-X555LB kernel: [637872.444869] Get event status notification: 4a 01 00 00 10 00 00 00 08 00
Jan 22 10:27:53 arcane-X555LB kernel: [637872.444877] ata2.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 14 pio 16392 in
Jan 22 10:27:53 arcane-X555LB kernel: [637872.444877]          res 50/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x10 (ATA bus error)
Jan 22 10:27:53 arcane-X555LB kernel: [637872.444878] ata2.00: status: { DRDY }
Jan 22 10:27:53 arcane-X555LB kernel: [637872.444882] ata2: hard resetting link
Jan 22 10:27:53 arcane-X555LB kernel: [637873.168661] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jan 22 10:27:53 arcane-X555LB kernel: [637873.174767] ata2.00: configured for UDMA/100
Jan 22 10:27:53 arcane-X555LB kernel: [637873.192654] ata2: EH complete
```

This is a new computer purchased in September, from Newegg, with an HDD hard disk. According to the SMART data the disk is okay and has passed all its test, but the error continues to occur in the kernel logs, using kernel 3.13, which is the only kernel that the wireless AND the graphics card can work together in without crashing. 

The error first appeared a few weeks ago, when my computer crashed randomly, with that being the only thing occurring before the crash that was out of the ordinary. The subsequent logs in kernel have not caused any issues: no freezing, crashing, error messages, or other.

Today, however, firefox crashed and afterwards, I was unable to open any program on the computer except for files. I tried to open system monitor and it popped up for a second before closing, with no error message or report. After rebooting, there was a disk error where fsk was not mounted, and after hitting the 'self fix' key it rebooted and now works fine.

Although it is passing the Smart Tests I know that can be misleading. Is this a bug or a hard drive failure? My system's specific specs:

Ubuntu 14.04 64-bit, Nvidia Geforce 940m, Intel Core i5-5200U, 750 GB HDD card. I dual boot Windows 10 and Ubuntu, though I never load Windows. I will note the firefox crash and subsequent inability to open applications occurred after an ordinary update, but I never checked what 'was' updated at the time and if it could be related. There was no error report after logging back in, and things seem to be functioning properly now. 

A few other sections of the kernel logs I am not sure about are these messages:
```
Jan 22 13:44:17 arcane-X555LB kernel: [    0.656192] ata1: SATA max UDMA/133 abar m2048@0xa3322000 port 0xa3322100 irq 63
Jan 22 13:44:17 arcane-X555LB kernel: [    0.656195] ata2: SATA max UDMA/133 abar m2048@0xa3322000 port 0xa3322180 irq 63
Jan 22 13:44:17 arcane-X555LB kernel: [    0.656196] ata3: DUMMY
Jan 22 13:44:17 arcane-X555LB kernel: [    0.656198] ata4: DUMMY
```

Is 'dummy' something to worry about?

```
Jan 22 13:44:17 arcane-X555LB kernel: [    0.255742] system 00:06: [io  0x1800-0x18fe] could not be reserved
Jan 22 13:44:17 arcane-X555LB kernel: [    0.255744] system 00:06: [io  0x164e-0x164f] has been reserved
Jan 22 13:44:17 arcane-X555LB kernel: [    0.255746] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
Jan 22 13:44:17 arcane-X555LB kernel: [    0.255785] pnp 00:07: Plug and Play ACPI device, IDs PNP0b00 (active)
Jan 22 13:44:17 arcane-X555LB kernel: [    0.255817] system 00:08: [io  0x1854-0x1857] has been reserved
Jan 22 13:44:17 arcane-X555LB kernel: [    0.255819] system 00:08: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
Jan 22 13:44:17 arcane-X555LB kernel: [    0.255939] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
Jan 22 13:44:17 arcane-X555LB kernel: [    0.255941] system 00:09: [mem 0xfed10000-0xfed17fff] has been reserved
Jan 22 13:44:17 arcane-X555LB kernel: [    0.255942] system 00:09: [mem 0xfed18000-0xfed18fff] has been reserved
Jan 22 13:44:17 arcane-X555LB kernel: [    0.255944] system 00:09: [mem 0xfed19000-0xfed19fff] has been reserved
Jan 22 13:44:17 arcane-X555LB kernel: [    0.255945] system 00:09: [mem 0xf8000000-0xfbffffff] has been reserved
Jan 22 13:44:17 arcane-X555LB kernel: [    0.255947] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
Jan 22 13:44:17 arcane-X555LB kernel: [    0.255949] system 00:09: [mem 0xfed90000-0xfed93fff] could not be reserved
Jan 22 13:44:17 arcane-X555LB kernel: [    0.255950] system 00:09: [mem 0xfed45000-0xfed8ffff] has been reserved
Jan 22 13:44:17 arcane-X555LB kernel: [    0.255952] system 00:09: [mem 0xff000000-0xffffffff] has been reserved
Jan 22 13:44:17 arcane-X555LB kernel: [    0.255953] system 00:09: [mem 0xfee00000-0xfeefffff] could not be reserved
Jan 22 13:44:17 arcane-X555LB kernel: [    0.255955] system 00:09: [mem 0xa0010000-0xa001ffff] has been reserved
Jan 22 13:44:17 arcane-X555LB kernel: [    0.255956] system 00:09: [mem 0xa0000000-0xa000ffff] has been reserved
Jan 22 13:44:17 arcane-X555LB kernel: [    0.255958] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
Jan 22 13:44:17 arcane-X555LB kernel: [    0.256286] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
```

Is it normal for things to 'not be reserved'?

I obviously know nothing about this stuff so any information that helps is appreciated. I do have a hardware warranty from Newegg but I am unsure whether it is 'voided' or not for installing Ubuntu.

---

### Post by mistcloud-misty on 2016-01-24
After installing Gsmartcontrol to search for more information I found two logged errors on the hard drive history in that application, both called "CRC erorrs", caused by error in 'reading'. After taking some advice from a friend I downloaded Ubuntu 15.10 on a drive, reinstalled it over 14.04 (completely erasing that part of the OS). The errors no longer appear in kernel logs, and neither do the frequent (often every 30minutes to an hour) kernel dumps caused by intel. I have an additionally proprietary driver for Intel and everything functions perfectly together. It seems 14.04 was not very suitable with this computer altogether, but 15.10 works almost perfectly.

As of now I'll say the problem is fixed, and hopefully might help some others who have the same problem.

---

### Post by Yellow Pasque on 2016-01-25
> **mistcloud-misty said:**
> Is 'dummy' something to worry about?
Only if you actually had devices connected to those SATA ports.

> Is it normal for things to 'not be reserved'?
Yes.

> It seems 14.04 was not very suitable with this computer altogether
Yeah, I'm not sure why people get brand new hardware and then want to run a 2 year old version on it. I know the LTS kernel and such gets updated, but that's not always sufficient. I understand why someone might want to use an LTS release, but at least wait for an LTS release that was released **after** your hardware.

---

