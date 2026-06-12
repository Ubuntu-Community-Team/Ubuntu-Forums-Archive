---
title: "sata cdrom unreachable after suspend"
date: 2006-11-17
forum: Hardware &amp; Laptops
---

### Post by vob on 2006-11-17
Hi,

I am running Kubuntu 6.06 on a Dell D620 laptop, which has a SATA CDROM, which usually works fine and as expected. However, when the system comes back after suspend, the cdrom is gone and can't be mounted anymore.

In /var/log/messages I find the following on startup
```
 kernel: [17179572.812000] scsi0 : ata_piix
 kernel: [17179572.812000]   Vendor: ATA       Model: SAMSUNG HM080II   Rev: YE10
 kernel: [17179572.812000]   Type:   Direct-Access                      ANSI SCSI revisi

 kernel: [17179572.812000] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xBFA8 irq

 kernel: [17179573.132000] ata2: dev 0 ATAPI, max UDMA/33
 kernel: [17179573.136000] ata2: dev 0 configured for UDMA/33
 kernel: [17179573.136000] scsi1 : ata_piix
 kernel: [17179573.136000]   Vendor: PHILIPS   Model: DVD+-RW SDVD8820  Rev: AD15
 kernel: [17179573.136000]   Type:   CD-ROM                             ANSI SCSI revisi

 kernel: [17179573.144000] Driver 'sd' needs updating - please use bus_type methods
 kernel: [17179573.144000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
 kernel: [17179573.144000] SCSI device sda: drive cache: write back
 kernel: [17179573.144000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
 kernel: [17179573.144000] SCSI device sda: drive cache: write back
 kernel: [17179573.144000]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 sda8 >
 kernel: [17179573.316000] sd 0:0:0:0: Attached scsi disk sda

```

and a little further down
```
 kernel: [17179580.552000] sd 0:0:0:0: Attached scsi generic sg0 type 0
 kernel: [17179580.552000]  1:0:0:0: Attached scsi generic sg1 type 5
 kernel: [17179580.912000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
 kernel: [17179580.912000] Uniform CD-ROM driver Revision: 3.20

```

Wher coming back from a suspend I found this yesterday
```
kernel: [17183720.896000] ata2: PIO error
 kernel: [17183720.900000] sr: Current [descriptor]: sense key: No Sense
 kernel: [17183720.900000]     Additional sense: No additional sense information

```

while today I only got
```
 kernel: [17191053.904000] ata2: dev 0 ATAPI, max UDMA/33
 kernel: [17191053.908000] ata2: dev 0 configured for UDMA/33

```

and nothing about sr. Nevertheless, the cdrom is gone today as well.

Any ideas what to do to get my cdrom back to work wothout having to reboot? Thanks in advance!

---

### Post by vob on 2006-12-11
Well, although the problem itself is not solved, I recently discovered a workaround: I just insert a CDRom and suspend the machine once again. Upon wake-up, the CD is detected and works fine.

---

### Post by chuvisco on 2007-01-04
I am having a similar problem with Edgy.  Neither my CD nor DVD drives are accessible after suspend.  In fact, if I do try to access either of them after suspend, the computer locks up hard and I have to turn it off using the power button.  Has anyone else seen anything like this?

---

