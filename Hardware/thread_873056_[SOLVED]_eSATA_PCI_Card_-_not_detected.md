---
title: "[SOLVED] eSATA PCI Card - not detected?"
date: 2008-07-28
forum: Hardware
---

### Post by CheeseAndToast on 2008-07-28
Hi All, 

I've just installed the new version of ubuntu 8.04.

I'm trying to get my external hard drive working, its a Seagate 500GB eSATA External Hard Disk, which is connected via an eSATA pci card.

I can't see the drive in "my computer"  I know it work as i use it on windows.

Any ideas?


See FDISK output:

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x03430342

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16824   135138748+   7  HPFS/NTFS
/dev/sda2           16825       24321    60219652+   5  Extended
/dev/sda5           16825       24009    57713481   83  Linux
/dev/sda6           24010       24321     2506108+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9d015d38

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001    c  W95 FAT32 (LBA)

---

### Post by markbuntu on 2008-07-28
Check in the logs to see if the pci card is being detected at boot. System/Administration/System Log

---

### Post by CheeseAndToast on 2008-07-29
Jul 29 22:11:44 ProfessorSingh783 kernel: [29863.442061] ata1: port is slow to respond, please be patient (Status 0xff)
Jul 29 22:11:47 ProfessorSingh783 kernel: [29866.745140] ata1: soft resetting link
Jul 29 22:11:47 ProfessorSingh783 kernel: [29866.901099] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Jul 29 22:11:47 ProfessorSingh783 kernel: [29866.944459] ata1.00: ATA-7: ST3500641AS, 3.AAE, max UDMA/133
Jul 29 22:11:47 ProfessorSingh783 kernel: [29866.944464] ata1.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 0/32)
Jul 29 22:11:47 ProfessorSingh783 kernel: [29867.027730] ata1.00: configured for UDMA/133
Jul 29 22:11:47 ProfessorSingh783 kernel: [29867.027740] ata1: EH complete
Jul 29 22:11:47 ProfessorSingh783 kernel: [29867.027887] scsi 0:0:0:0: Direct-Access     ATA      ST3500641AS      3.AA PQ: 0 ANSI: 5
Jul 29 22:11:47 ProfessorSingh783 kernel: [29867.028555] sd 0:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
Jul 29 22:11:47 ProfessorSingh783 kernel: [29867.028572] sd 0:0:0:0: [sdb] Write Protect is off
Jul 29 22:11:47 ProfessorSingh783 kernel: [29867.028575] sd 0:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Jul 29 22:11:47 ProfessorSingh783 kernel: [29867.028593] sd 0:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 29 22:11:47 ProfessorSingh783 kernel: [29867.028656] sd 0:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
Jul 29 22:11:47 ProfessorSingh783 kernel: [29867.028667] sd 0:0:0:0: [sdb] Write Protect is off
Jul 29 22:11:47 ProfessorSingh783 kernel: [29867.028670] sd 0:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Jul 29 22:11:47 ProfessorSingh783 kernel: [29867.028687] sd 0:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 29 22:11:48 ProfessorSingh783 kernel: [29867.028691]  sdb: sdb1
Jul 29 22:11:48 ProfessorSingh783 kernel: [29867.112396] sd 0:0:0:0: [sdb] Attached SCSI disk
Jul 29 22:11:48 ProfessorSingh783 kernel: [29867.112450] sd 0:0:0:0: Attached scsi generic sg2 type 0

---

### Post by markbuntu on 2008-07-29
It seems that Ubuntu is finding the drive OK.

If you do not have permissons set up for your current user to access the drive, it will not show up.

---

### Post by CheeseAndToast on 2008-07-31
Thanks for your reply, the user does have permissions to access external devices automatically.  What elese can i assign permissions?

---

### Post by markbuntu on 2008-07-31
Well, that is being treated as an internal drive, not external, check the permissions for mounting internal drives.

---

### Post by CheeseAndToast on 2008-07-31
> **markbuntu said:**
> Well, that is being treated as an internal drive, not external, check the permissions for mounting internal drives.

Where do i need to go to check that?   Sorry its all new to me!

Thanks

---

### Post by markbuntu on 2008-07-31
You can check that in 

System/Authorizations/storage/Mount file systems from internal drives.

Ubuntu/linux has a lot of built in security features which is what makes it so difficult to hack into and attack with viruses. A big part of that is permissions.

In System/Authorizations you can change the permissions for pretty much everything
and anybody, but you need to know the password to do that. Security, built in. I can be a pain sometimes but it makes you more secure.

---

### Post by CheeseAndToast on 2008-08-02
What Implicit/Explicit authorizations do i need to set?
I've given myself the following:

Mount file systems from removeable drives
Mount file systems from internal drives
Eject removable media

What constraints do i need to set?

From the sys log:

Aug  2 13:07:08 ProfessorSingh783 kernel: [  762.766110] ata1: soft resetting link
Aug  2 13:07:08 ProfessorSingh783 kernel: [  762.922083] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug  2 13:07:08 ProfessorSingh783 kernel: [  762.986943] ata1.00: ATA-7: ST3500641AS, 3.AAE, max UDMA/133
Aug  2 13:07:08 ProfessorSingh783 kernel: [  762.986950] ata1.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 0/32)
Aug  2 13:07:08 ProfessorSingh783 kernel: [  763.070223] ata1.00: configured for UDMA/133
Aug  2 13:07:08 ProfessorSingh783 kernel: [  763.070238] ata1: EH complete
Aug  2 13:07:08 ProfessorSingh783 kernel: [  763.070386] scsi 0:0:0:0: Direct-Access     ATA      ST3500641AS      3.AA PQ: 0 ANSI: 5
Aug  2 13:07:08 ProfessorSingh783 kernel: [  763.071056] sd 0:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
Aug  2 13:07:08 ProfessorSingh783 kernel: [  763.071073] sd 0:0:0:0: [sdb] Write Protect is off
Aug  2 13:07:08 ProfessorSingh783 kernel: [  763.071075] sd 0:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Aug  2 13:07:08 ProfessorSingh783 kernel: [  763.071094] sd 0:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug  2 13:07:08 ProfessorSingh783 kernel: [  763.071154] sd 0:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
Aug  2 13:07:08 ProfessorSingh783 kernel: [  763.071165] sd 0:0:0:0: [sdb] Write Protect is off
Aug  2 13:07:08 ProfessorSingh783 kernel: [  763.071168] sd 0:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Aug  2 13:07:08 ProfessorSingh783 kernel: [  763.071184] sd 0:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug  2 13:07:08 ProfessorSingh783 NetworkManager: <debug> [1217678828.921009] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_105a_3d73_scsi_host'). 
Aug  2 13:07:08 ProfessorSingh783 kernel: [  763.071188]  sdb: sdb1
Aug  2 13:07:08 ProfessorSingh783 kernel: [  763.156168] sd 0:0:0:0: [sdb] Attached SCSI disk
Aug  2 13:07:08 ProfessorSingh783 kernel: [  763.156220] sd 0:0:0:0: Attached scsi generic sg2 type 0
Aug  2 13:07:08 ProfessorSingh783 NetworkManager: <debug> [1217678828.925988] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_105a_3d73_scsi_host_scsi_device_lun0'). 
Aug  2 13:07:08 ProfessorSingh783 NetworkManager: <debug> [1217678828.957234] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_105a_3d73_scsi_host_scsi_device_lun0_scsi_generic'). 
Aug  2 13:07:09 ProfessorSingh783 NetworkManager: <debug> [1217678829.077373] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_ST3500641AS_3PM18K7X'). 
Aug  2 13:07:09 ProfessorSingh783 NetworkManager: <debug> [1217678829.155796] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part1_size_500105217024').

---

### Post by CheeseAndToast on 2008-08-02
all, fixed by following :

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

thanks

---

### Post by markbuntu on 2008-08-02
Hooray for you!. 

I have a friend called BeansAndToast, you aren't by chance related are you?

Please mark this thread as solved if you don't mind.

---

