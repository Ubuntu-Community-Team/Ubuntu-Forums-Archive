---
title: "Adaptec SCSI card and long boot"
date: 2006-12-05
forum: Hardware &amp; Laptops
---

### Post by karaluh on 2006-12-05
Dapper, 2.6.15-27-386. System freezes for 41 seconds on "Mounting root filesystem". I've found, that it's happening because of Adaptec's 39320D SCSI card. If it's plug out, system boots normaly. I wanted to investigate the details, so i've disabled splash and quiet mode, but all the mesages disappear too quickly. I tried bootlogd, but it starts to log much too late for being useful. If you know how to tune bootlogd, know any other way to log boot messages or have some tips regarding the main problem, help please.

I used dmesg and peace of paper for this :)

[17179578.776000] P0P4 MC97 USB1 USB2 USB3 USB4 EUSB PS2K PS2M ILAN 
[17179578.776000] ACPI: (supports S0 S1 S3 S4 S5)
[17179578.776000] Freeing unused kernel memory: 288k freed
[17179578.824000] Capability LSM initialized
[17179579.332000] SCSI subsystem initialized
[17179579.336000] ACPI: PCI Interrupt 0000:02:0a.0[A] -> GSI 22 (level, low) -> IRQ 169

boot stops here for a while

[17179594.564000] scsi0 : Adaptec AIC79XX PCI-X SCSI HBA DRIVER, Rev 3.0
[17179594.564000]         <Adaptec 39320D Ultra320 SCSI adapter>
[17179594.564000]         aic7902: Ultra320 Wide Channel A, SCSI Id=7, PCI 33 or 66Mhz, 512 SCBs
[17179594.564000] 
[17179597.904000]   Vendor: FUJITSU   Model: MAP3367NP         Rev: 0108
[17179597.908000]   Type:   Direct-Access                      ANSI SCSI revision: 03
[17179597.908000]  target0:0:14: asynchronous
[17179597.908000] scsi0:A:14:0: Tagged Queuing enabled.  Depth 32
[17179597.908000]  target0:0:14: Beginning Domain Validation
[17179597.912000]  target0:0:14: wide asynchronous
[17179597.912000]  target0:0:14: FAST-160 WIDE SCSI 320.0 MB/s DT IU QAS PCOMP (6.25 ns, offset 127)
[17179597.928000]  target0:0:14: Ending Domain Validation
[17179597.932000]   Vendor: FUJITSU   Model: MAP3367NP         Rev: 0108
[17179597.932000]   Type:   Direct-Access                      ANSI SCSI revision: 03
[17179597.932000]  target0:0:15: asynchronous
[17179597.932000] scsi0:A:15:0: Tagged Queuing enabled.  Depth 32
[17179597.932000]  target0:0:15: Beginning Domain Validation
[17179597.936000]  target0:0:15: wide asynchronous
[17179597.940000]  target0:0:15: FAST-160 WIDE SCSI 320.0 MB/s DT IU QAS PCOMP (6.25 ns, offset 127)
[17179597.956000]  target0:0:15: Ending Domain Validation
[17179597.960000] ACPI: PCI Interrupt 0000:02:0a.1[B] -> GSI 23 (level, low) -> IRQ 177

boot stops here for a while

[17179613.188000] scsi1 : Adaptec AIC79XX PCI-X SCSI HBA DRIVER, Rev 3.0
[17179613.188000]         <Adaptec 39320D Ultra320 SCSI adapter>
[17179613.188000]         aic7902: Ultra320 Wide Channel B, SCSI Id=7, PCI 33 or 66Mhz, 512 SCBs
[17179613.188000] 
[17179617.068000] Driver 'sd' needs updating - please use bus_type methods
[17179617.072000] SCSI device sda: 71775284 512-byte hdwr sectors (36749 MB)
[17179617.072000] SCSI device sda: drive cache: write back
[17179617.076000] SCSI device sda: 71775284 512-byte hdwr sectors (36749 MB)
[17179617.080000] SCSI device sda: drive cache: write back
[17179617.080000]  sda: sda1 sda2 sda3 < sda5 sda6 > sda4
[17179617.104000] sd 0:0:14:0: Attached scsi disk sda
[17179617.104000] SCSI device sdb: 71775284 512-byte hdwr sectors (36749 MB)
[17179617.104000] SCSI device sdb: drive cache: write back
[17179617.108000] SCSI device sdb: 71775284 512-byte hdwr sectors (36749 MB)
[17179617.112000] SCSI device sdb: drive cache: write back
[17179617.112000]  sdb: sdb1 sdb2 sdb3 < sdb5 sdb6 > sdb4
[17179617.132000] sd 0:0:15:0: Attached scsi disk sdb
[17179617.348000] ICH5: IDE controller at PCI slot 0000:00:1f.1

Here is the sollution:
[https://launchpad.net/ubuntu/+bug/79542](https://launchpad.net/ubuntu/+bug/79542)

---

