---
title: "IDE drives not detected on Heron"
date: 2008-08-24
forum: Hardware
---

### Post by marisol on 2008-08-24
Hello, 
installed Heron from 8.04.1 desktop install disk for my dad, he's tired of XP getting slower and slower. 

after getting things up an running on on ABIT IS7 MB with a new Seagate ST3250410AS ( SATA ) and Plextor DVDR PX-820SA ( SATA ) it was time to move his XP drives (2 IDE) into the new situation.

no way, no how can I see the IDE drives detected. 
BIOS detects them, Heron does not.
yes, I know what I am doing re: cable attachment, master/slave etc. all is proper. both drives are connected to IDE Channel 1 as master and slave and  are functional.

I suspect something is amiss in the kernel build, based on this:
----------------------------------------------------------------------
> dmesg|egrep -i 'ata|hd'
[   28.886357] libata version 3.00 loaded.
[   28.999635] ata_piix 0000:00:1f.2: version 2.12
[   28.999644] ata_piix 0000:00:1f.2: MAP [ IDE IDE P0 P1 ]
[   29.001684] scsi0 : ata_piix
[   29.001822] scsi1 : ata_piix
[   29.002845] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[   29.002852] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[   29.486173] ata2.00: ATA-7: ST3250410AS, 3.AAF, max UDMA/133
[   29.486180] ata2.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   29.486216] ata2.01: ATAPI: PLEXTOR DVDR   PX-820SA, 1.00, max UDMA/100
[   29.502152] ata2.00: configured for UDMA/133
[   29.673546] ata2.01: configured for UDMA/100
[   29.673705] scsi 1:0:0:0: Direct-Access     ATA      ST3250410AS      3.AA PQ: 0 ANSI: 5
[   30.206488] EXT3-fs: mounted filesystem with ordered data mode.
----------------------------------------------------------------------

as you can see, no mention of the IDE pair.

/dev has no hd[a-z][0-9]* entrys 

and there is this:
> find /dev/disk/
/dev/disk/
/dev/disk/by-uuid
/dev/disk/by-uuid/6cbfc0a8-efd1-44eb-a2a4-8781a02f4783
/dev/disk/by-uuid/09c03bec-d4c7-4d1e-abc2-4e7560ed7c3f
/dev/disk/by-id
/dev/disk/by-id/ata-ST3250410AS_6RY666BR-part5
/dev/disk/by-id/scsi-1ATA_ST3250410AS_6RY666BR-part5
/dev/disk/by-id/ata-ST3250410AS_6RY666BR-part2
/dev/disk/by-id/scsi-1ATA_ST3250410AS_6RY666BR-part2
/dev/disk/by-id/ata-ST3250410AS_6RY666BR-part1
/dev/disk/by-id/scsi-1ATA_ST3250410AS_6RY666BR-part1
/dev/disk/by-id/ata-ST3250410AS_6RY666BR
/dev/disk/by-id/scsi-1ATA_ST3250410AS_6RY666BR
/dev/disk/by-path
/dev/disk/by-path/pci-0000:00:1f.2-scsi-1:0:0:0-part5
/dev/disk/by-path/pci-0000:00:1f.2-scsi-1:0:0:0-part2
/dev/disk/by-path/pci-0000:00:1f.2-scsi-1:0:0:0-part1
/dev/disk/by-path/pci-0000:00:1f.2-scsi-1:0:0:0
/dev/disk/by-path/pci-0000:00:1f.2-scsi-1:0:1:0



more info:

> cat /proc/version
Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11 23:41:49 UTC 2008

> cat /etc/issue
Ubuntu 8.04.1 \n \l


> fdisk -l;echo '--------';blkid;echo '--------';lshw -C disk
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d308d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29265   235071081   83  Linux
/dev/sda2           29266       30401     9124920    5  Extended
/dev/sda5           29266       30401     9124888+  82  Linux swap / Solaris
--------
/dev/sda1: UUID="09c03bec-d4c7-4d1e-abc2-4e7560ed7c3f" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="6cbfc0a8-efd1-44eb-a2a4-8781a02f4783" 
--------
  *-disk                  
       description: ATA Disk
       product: ST3250410AS
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/sda
       version: 3.AA
       serial: 6RY666BR
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000d308d
  *-cdrom
       description: DVD-RAM writer
       product: DVDR   PX-820SA
       vendor: PLEXTOR
       physical id: 0.1.0
       bus info: scsi@1:0.1.0
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.00
       serial: [PLEXTOR DVDR   PX-820SA 1.0002/21/08
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=open


anybody seen this or have any clues? Unfortunately, I am not physically near the machine, we set this up on a visit and I can only work on it via ssh now.
is IDE support removed in the 2.6.24-19-generic kernel config or does the installer detect the absence of IDE devices and leave it out ( i don't know how the ubuntu installation is set up ), only compiling what is needed?

This sort of thing ( common hardware detection ) used to be really, really solid on all distros. what happened?

tia,
marisol

---

### Post by jpkotta on 2008-08-24
Almost all drives show up as /dev/sd? now.  The drivers for hard drives have been unified under libata.  When you say "IDE" you really mean PATA (Parallel ATA).  To make things more confusing, Linux reuses the SCSI layer in libata, so the drives come up as sd?.  

Now, something isn't quite right.  I suspect that the ata_piix driver and libata are fighting for control of the drives.  Try blacklisting ata_piix with
```
sudo -i
echo "blacklist ata_piix" >> /etc/modprobe.d/blacklist-local
exit
```

Since these are probably getting loaded in the initrd, you might want to try
```
sudo update-initramfs
```

---

### Post by marisol on 2008-08-26
thanks jpkotta,
i did as you suggested, blacklisted ata_piix and ran
> update-initramfs -u 

to update. 

no dice, he got a busybox-type shell and we had to boot to the install cd to recover the functional initrd.

---

### Post by jpkotta on 2008-08-26
That's weird.  What happens when ata_piix is blacklisted and the PATA drives are not connected/disabled in the BIOS?  What happens if you use the BIOS to put the controller in AHCI mode?

---

### Post by marisol on 2008-08-27
ahh..... problem solved. I'm not clear about what was going on, but dad set both drives to CS and things got right. SATA is now sdc and the PATA's are sd{a,b} .

Thank you for your time. Very sorry bout that.

---

