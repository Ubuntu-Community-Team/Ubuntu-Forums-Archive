---
title: "Adaptec 2400A ATA Raid on Ubuntu Daper Server"
date: 2006-11-27
forum: Hardware &amp; Laptops
---

### Post by 3DLover on 2006-11-27
Hi all,

  I have a fresh install of 6.01.1 Server i386 that I have fully upgraded to kernel 2.6.15-27-server.  In this machine I have an Adaptec 2400A with a 4-drive RAID-5 configured.  The installer found my raid and I formatted an ext-3 partition.  I installed Ubuntu to a single HDD pluged into the motherboard, and then configured the raid to be mounted in /mnt/bigraid.  The install routine then added the raid volume to my fstab as /dev/i2o/hda1  After the install finished I rebooted and got a bunch of errors about /dev/i2o/hda1 not being found.

  Attached is a full dmesg dump, but I have included a relevant snippet here that is probably part of my problem.

=============================================
TID 521  Vendor: ADAPTEC      Device: RAID-5       Rev: 3A0L
scsi0 : Vendor: Adaptec  Model: 2400A            FW:3A0L
  Vendor: ADAPTEC   Model: RAID-5            Rev: 3A0L
  Type:   Direct-Access                      ANSI SCSI revision: 02
Driver 'sd' needs updating - please use bus_type methods
I2O subsystem v1.288
i2o: max drivers = 8
i2o: Checking for PCI I2O controllers...
ACPI: PCI Interrupt 0000:01:09.0[A] -> Link [APC2] -> GSI 17 (level, high) -> IRQ 201
iop0: controller found (0000:01:09.0)
iop0: limit sectors per request to 256
iop0: using 64-bit DMA
PCI: Unable to reserve mem region #1:8000000@d8000000 for device 0000:01:09.0
iop0: device already claimed
iop0: DMA / IO allocation for I2O controller  failed
SCSI device sda: 1172164608 512-byte hdwr sectors (600148 MB)
sda: asking for cache data failed
sda: assuming drive cache: write through
SCSI device sda: 1172164608 512-byte hdwr sectors (600148 MB)
sda: asking for cache data failed
sda: assuming drive cache: write through
 sda: sda1
sd 0:0:0:0: Attached scsi disk sda
=============================================

  As you can see, the i2o starts a scan for devices, and then iop0 finds a device and then errors with the "device already claimed" message.  I did some googling for i2o and iop0 and found a few postings mentioning that these two drivers can conflict with each other, and that I should disable one of them.  I presume that I should disable the iop0 since the Ubuntu installer originally found my device with the i2o, but this is just a guess. I don't know how to disable one or the other, and I really don't know which is 'better'.

  I have found that I can access my raid as /dev/sda1.  It seems to work and I can copy files to/from the raid using this device.  Should I try to fix the i2o/iop0 issue so that I can access it with /dev/i2o/hda1, or ignore the errors and access it as /dev/sda1?  Is either i2o or iop0 better than /dev/sda1?  Is disabling either i2o or iop0 the best way to resolve this, and if so, how do I go about doing this?  Can I use raidutils without i2o/iop0?

  I have also noticed that there are a lot of "Misaligned resource pointer" error messages in my dmesg dump.  I understand that these may have something to with ACPI, but again, this is a new error for me and I don't know what (if anything) I should do about it.  Would these errors have anything to do with my RAID issues?

Thanks,
  Ray

---

