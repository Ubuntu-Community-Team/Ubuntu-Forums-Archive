---
title: "Mount failed on new larger primary HD install"
date: 2008-09-19
forum: Hardware
---

### Post by gerryg001 on 2008-09-19
An older Sager Np4750 w/ phoenix 4.06 10/2004. Original 60Gb drive died. New one is 160Gb. Sager says bios only supports 128Gb, which Ubuntu reports. On Ubuntu 8.04 install, format completes, but can't mount file system. HD test was okay. Is there any place to go here, other than trying to find the original drive type?

Tried CD-boot, and direct partition and format okay.
Then hit install, and failed to mount again.

In log
wrong ufstype
ufs_read_super: bad magic number
hfs:can't find HFS filesystem on dev sda1
ACPI exception (thermal-0471):AE_NOT_FOUND

and so on

---

### Post by IntuitiveNipple on 2008-09-19
If the disk is organised with multiple partitions, such that the boot partition is at the start of the disk and is smaller than the maximum size the BIOS can address, the disk can be used without issues by Linux.

The problem comes when the disk has one large partition, or the boot partition goes beyond the limit the BIOS can read (in which case it wraps around to the start of the disk!).

I'd suggest configuring and installing it so it has:

#1 256MB ext3 /boot
#2 2000MB swap
#3 12GB ext3 /
#4 remaining ext3 /home

alternatively you could use LVM so #3 uses the remaining space and inside that is a volume group and logical volumes for /, /var, /home and a little left over for growing one of the volumes later if needed. LVM is a whole other story though :)

---

### Post by gerryg001 on 2008-09-19
Well, gparted really isn't going to allow you to try and use anything past the bios size, anyway. So partitioning smaller than the max from bios doesn't apply. After the first failure, I dropped back to a single, 8Gb partition, and that also failed.

Seem to recall that years (rather, decades) ago, I had to modify a table created from bios info. The issue was that the bios was incorrectly stating the actual drive parameters, and that any attempt to address the drive using them caused failure. The LBA mapping did not align with the physical, so that only a small % of the bios size could be used during the initial install.

So, tried a single, 3Gb partition, and also failed.

Probably indicates more than just the cylinder/sector sizes are wrong from the bios. Might be able to boot from CD, modify the table, then do an install. Once installed, it should use its own tables instead of bios. At least that's what I seem to remember.

Anybody agree, and remember how to do that?

---

### Post by IntuitiveNipple on 2008-09-19
Try using fdisk or cfdisk in a terminal, see what CHS/LBA values they report.

Check /var/log/kern.log in case there are hidden disk errors being reported that indicate something more.

Also, what does /var/log/dmesg show as the detected parameters for that disk when the kernel module loads? It'll be something like:
```

[   18.309582] ata3.00: ATA-7: FUJITSU MHV2200BT, 0000004F, max UDMA/100
[   18.309588] ata3.00: 390721968 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   18.324579] ata3.00: configured for UDMA/100
[   18.503878] sd 2:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[   18.503911] sd 2:0:0:0: [sda] Write Protect is off
[   18.503915] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   18.503946] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

```

---

### Post by gerryg001 on 2008-09-19
Drive model doesn't list, but seems to cross to a 5K160
HTS541616J9AT00
which has
Capacity (GB)1  	160 / 120 / 80 / 60 / 40  	
Sector size (Bytes) 	512 	
Recording zones 	16 	
Data heads (physical) 	4 / 4 / 2 / 2 / 1 	
Data Disks 	2 / 2 / 1 / 1 / 1
UDMA 100

kern.log didn't show much, but dmesg did:
Log shows:
ata1.00: failed to set max address (err_mask=0x1)
ata1.00: device aborted resize (251657728 -> 312581808) skipping HPA handling
ata1.00: ATA-7: Hitabhh HTR541616J8AT00, RB40@70H, max UDMA/100
ata1.00: 251657728 sectors, multi 0: LBA48
ata1.00: configured for UDMA/100
...
[sda] write cache: enables, read cache: enabled, doesn't support DPO or FUA
[sda] mode sense: 00 3a 00 00
ldm_validate_partition_table(): Disk read failed.
Dev sda: unable to read RDB block 0
unable to read partition table

which looks a bit upsetting, if that's also a physical block 0. I'm getting the impression of a hardware controller failure. Any thoughts there?

disk /dev/sda 128.8 GB
255 heads, 63 s/t 15664 cyl
units = cyl of 16065 * 512 = 8225280 bytes
/dev/sda1 start 1   end 365  blocks 2931831   ID 83

---

### Post by IntuitiveNipple on 2008-09-19
> **gerryg001 said:**
> 
ata1.00: failed to set max address (err_mask=0x1)
ata1.00: device aborted resize (251657728 -> 312581808) skipping HPA handling
This error is generated in drivers/ata/libata-core.c::ata_hpa_resize().

It seems the drive is reporting an HPA (Host Protected Area) but the driver is unable to unlock it.
```

  /* let's unlock HPA */
  rc = ata_set_max_sectors(dev, native_sectors);
  if (rc == -EACCES) {
    /* if device aborted the command, skip HPA resizing */
    ata_dev_printk(dev, KERN_WARNING, "device aborted resize "
      "(%llu -> %llu), skipping HPA handling\n",
      (unsigned long long)sectors,
      (unsigned long long)native_sectors);
    dev->horkage |= ATA_HORKAGE_BROKEN_HPA;
    return 0;
  }

```
It is possible this is happening because of the BIOS size issue but I think it unlikely since the BIOS isn't involved at this point - the driver has got direct control.

The libata module has an HPA parameter:
```

 modinfo libata | grep HPA
parm:           ignore_hpa:Ignore HPA limit (0=keep BIOS limits, 1=ignore limits, using full disk, default) (int)

```
Looking in the source-code shows that warnings and errors are issued about HPA, so check the log for those:
```

grep -i hpa /var/log/dmesg

```

---

### Post by gerryg001 on 2008-09-19
Will do, but will be awhile. I downloaded Hitachi's drive tester as an ISO. It also reports the bios reduced 128Gb. Going to run their full test, then attempt to erase the drive, to see if they catch any failures at that level.

This will take some time, but at least I'll know if there's a chance of winning this one. The quick test passed, now scanning the whole drive. As these are non-destructive tests, the erase might catch a write failure (though I don't know if it verifies).

Just realized the CD boot should support a memory stick, so I can dump the logs to another machine. It'll be much easier to paste (not retype) into this screen. Bought and started setting up a desktop last week, just in case my laptop died, so of course it did. Going to try and find some sources, and look over your reference further.

Thanks much for your help, when I last did this stuff, Linux was not yet born.

---

### Post by IntuitiveNipple on 2008-09-19
The trick in diagnosing these issues is to chase the logs and enable all debug options you can find - oh and being 100% precise in reporting details because even a missing semi-colon can make a big difference :)

---

### Post by gerryg001 on 2008-09-20
Hitachi's tests said the disk is okay. But, when I went to erase it, the Hitachi disk tester refused, saying the drive is not Hitachi. Go figure!

You asked for:
gerryg@taca:/media/disk/LaptopLogs$ grep -i hpa dmesg
[   39.791041] ata1.00: device aborted resize (251657728 -> 312581808), skipping HPA handling
 
and kern.log has
Sep 19 21:31:41 ubuntu kernel: [   39.628551] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x1c60 irq 14
Sep 19 21:31:41 ubuntu kernel: [   39.628557] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x1c68 irq 15
Sep 19 21:31:41 ubuntu kernel: [   39.791032] ata1.00: failed to set max address (err_mask=0x1)
Sep 19 21:31:41 ubuntu kernel: [   39.791041] ata1.00: device aborted resize (251657728 -> 312581808), skipping HPA handling
Sep 19 21:31:41 ubuntu kernel: [   39.791052] ata1.00: ATA-7: Hitabhh HTR541616J8AT00, RB4O@70H, max UDMA/100
Sep 19 21:31:41 ubuntu kernel: [   39.791059] ata1.00: 251657728 sectors, multi 0: LBA48 
Sep 19 21:31:41 ubuntu kernel: [   39.806439] ata1.00: configured for UDMA/100

Looking further in kern.log, it gets ATA bus errors, and reconfigs the link down through UDMA/33.

From CD boot, gparted seems to partition/format okay. However, tried to mount a small partition formated ext3, and
kern.log (nothing in dmesg)

ACPI exception (thermal-0471): AE_NOT_FOUND
VFS: can't find ext3 filesystem on dev sda1

In line with this, gparted shows the filesystem unknown, even after it's formatted it.

Now where??
Is there a low-level sector read/write available somewhere?

Also, we have a coincidence factor here. The old drive failed, and the new one failed. Maybe I should put the old one back, and see if the exact same errors?

---

### Post by IntuitiveNipple on 2008-09-20
> **gerryg001 said:**
> 
Also, we have a coincidence factor here. The old drive failed, and the new one failed. Maybe I should put the old one back, and see if the exact same errors?
Yes, I'm wondering about the controller and/or cables... at least eliminate them as suspects :)

---

### Post by gerryg001 on 2008-09-20
As a laptop, there's just a right-angle adapter. I cleaned and reseated that early on. Checked laptop manual and cd's, and no mobo diagnostics. Just restored the original hard drive. From gparted, it sees the old partition, and the type, so it can read the disk. However, tried to partition a small area at the end, and it failed. Logs are somewhat different, but many items similar. Ran Hitachi's disk test on the old HD, and it passes there also.

So, coincidence factor says that I either have a broken pin/trace on the adapter, or the controller on the mobo is bad. Will call Sager on Monday. But, as this is 4 years old, replacement mobo may not be available, or may cost as much as a new laptop. If so, I'll pull it apart and do a visual on the mobo, then go and cry.

In the meantime, going to move the old HD to an old laptop, and see what I get. Thanks again for your help here.

And, if you happen to think of a solution, please don't hesitate to toss it in here:-)
Thanks,
Gerry

---

### Post by IntuitiveNipple on 2008-09-20
> **gerryg001 said:**
> So, coincidence factor says that I either have a broken pin/trace on the adapter, or the controller on the mobo is bad. Will call Sager on Monday. But, as this is 4 years old, replacement mobo may not be available, or may cost as much as a new laptop. If so, I'll pull it apart and do a visual on the mobo, then go and cry.

That's what I'd do. I'd suggest looking for sites of dry-joints and running some fresh solder on them - edge connectors with small amounts of flex are prime candidates for that. I've repaired many PDA docking connectors that way.

---

### Post by gerryg001 on 2008-09-20
Well, the old laptop had bios too old to recognize the drive. Oh well.

Adapter looked and tested good. Taking that laptop apart is a dog, so going to wait until I talk to Sager. I'm all set up here for surface mount repair and inspection, so it'll get a good pass under a microscope. Might as well kill some more time:-) It's just possible that Sager might have a refurb mobo that's cheap.

Budget won't stand a new one right now, so I'll just finish up the desktop. An E8400 duo with 8Gb ram and Ubuntu-64, 500Gb and virtualized XP. So I'm not hurting too bad. Just lucky I bought it when I did.

Thanks once again. I'll add more here next week if something changes.

---

