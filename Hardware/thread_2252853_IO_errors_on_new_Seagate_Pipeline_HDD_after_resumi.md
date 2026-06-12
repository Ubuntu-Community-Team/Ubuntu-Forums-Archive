---
title: "I/O errors on new Seagate Pipeline HDD after resuming from suspend Ubuntu 14.04"
date: 2014-11-15
forum: Hardware
---

### Post by vonbureck on 2014-11-15
I just replaced my previous HDD (a Hitachi 500 GB) with a Seagate Barracuda Pipeline 1 TB HDD (ST1000VM002). Everything worked fine previously, but now if I wake the system after suspending to RAM, the desktop takes about a minute to come up and the disk is unreadable (I/O errors if I try to access anything), so rebooting is the only solution. The new drive is on /dev/sdb and holds my /home partition, while the system is on a separate SSD on /dev/sda. Apart from the resume issue, the drive seems fine (SMART tests etc.), and it wakes from suspend just fine under Windows.

Here's the output from dmesg following the error:

[  187.482364] PM: Syncing filesystems ... done.
[  187.566929] PM: Preparing system for mem sleep
[  187.825835] Freezing user space processes ... (elapsed 0.002 seconds) done.
[  187.828430] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
[  187.829821] PM: Entering mem sleep
[  187.829856] Suspending console(s) (use no_console_suspend to debug)
[  187.830250] sd 1:0:0:0: [sdb] Synchronizing SCSI cache
[  187.830367] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[  187.830534] sd 1:0:0:0: [sdb] Stopping disk
[  187.830983] parport_pc 00:0a: disabled
[  187.831206] serial 00:09: disabled
[  187.831382] serial 00:08: disabled
[  187.831393] serial 00:08: System wakeup disabled by ACPI
[  187.833223] sd 0:0:0:0: [sda] Stopping disk
[  188.497776] PM: suspend of devices complete after 668.058 msecs
[  188.498073] PM: late suspend of devices complete after 0.291 msecs
[  188.498506] ehci-pci 0000:00:02.1: System wakeup enabled by ACPI
[  188.508765] ohci-pci 0000:00:02.0: System wakeup enabled by ACPI
[  188.519867] PM: noirq suspend of devices complete after 21.796 msecs
[  188.521209] ACPI: Preparing to enter system sleep state S3
[  188.784639] PM: Saving platform NVS memory
[  188.784665] Disabling non-boot CPUs ...
[  188.785184] Broke affinity for irq 21
[  188.786204] kvm: disabling virtualization on CPU1
[  188.786269] smpboot: CPU 1 is now offline
[  188.788423] kvm: disabling virtualization on CPU2
[  188.788458] smpboot: CPU 2 is now offline
[  188.790912] ACPI: Low-level resume complete
[  188.790975] PM: Restoring platform NVS memory
[  188.791617] PCI-DMA: Resuming GART IOMMU
[  188.791618] PCI-DMA: Restoring GART aperture settings
[  188.791792] LVT offset 1 assigned for vector 0x400
[  188.791800] IBS: LVT offset 1 assigned
[  188.791994] Enabling non-boot CPUs ...
[  188.792038] x86: Booting SMP configuration:
[  188.792039] smpboot: Booting Node 0 Processor 1 APIC 0x1
[  188.803090] kvm: enabling virtualization on CPU1
[  188.805417] CPU1 is up
[  188.805434] smpboot: Booting Node 0 Processor 2 APIC 0x2
[  188.816484] kvm: enabling virtualization on CPU2
[  188.818743] CPU2 is up
[  188.822313] ACPI: Waking up from system sleep state S3
[  188.833430] ohci-pci 0000:00:02.0: System wakeup disabled by ACPI
[  188.844453] ehci-pci 0000:00:02.1: System wakeup disabled by ACPI
[  188.844514] pci 0000:00:00.0: Found enabled HT MSI Mapping
[  188.866460] pci 0000:00:00.0: Found enabled HT MSI Mapping
[  188.866566] pci 0000:00:00.0: Found enabled HT MSI Mapping
[  188.866674] pci 0000:00:00.0: Found enabled HT MSI Mapping
[  188.877568] PM: noirq resume of devices complete after 55.042 msecs
[  188.877886] PM: early resume of devices complete after 0.237 msecs
[  188.879631] serial 00:08: activated
[  188.880802] ata4: port disabled--ignoring
[  188.881205] serial 00:09: activated
[  188.884249] parport_pc 00:0a: activated
[  189.038895] ata3.00: ACPI cmd ef/03:44:00:00:00:a0 (SET FEATURES) filtered out
[  189.038902] ata3.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[  189.038928] ata3: nv_mode_filter: 0x1f39f&0x1f39f->0x1f39f, BIOS=0x1f000 (0xc5000000) ACPI=0x1f01f (30:600:0x13)
[  189.044676] ata3.00: configured for UDMA/66
[  189.335113] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  189.354188] ata1.00: ACPI cmd ef/03:46:00:00:00:a0 (SET FEATURES) filtered out
[  189.380137] ata1.00: configured for UDMA/133
[  189.380214] sd 0:0:0:0: [sda] Starting disk
[  194.382858] ata2: link is slow to respond, please be patient (ready=0)
[  198.918956] ata2: SRST failed (errno=-16)
[  204.418429] ata2: link is slow to respond, please be patient (ready=0)
[  208.954526] ata2: SRST failed (errno=-16)
[  214.454003] ata2: link is slow to respond, please be patient (ready=0)
[  243.964078] ata2: SRST failed (errno=-16)
[  243.964082] ata2: limiting SATA link speed to 1.5 Gbps
[  249.004858] ata2: SRST failed (errno=-16)
[  249.015450] ata2: reset failed, giving up
[  249.015454] ata2.00: disabled
[  249.015523] sd 1:0:0:0: [sdb] Starting disk
[  249.015566] sd 1:0:0:0: [sdb] START_STOP FAILED
[  249.015570] sd 1:0:0:0: [sdb]  
[  249.015572] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[  249.015587] dpm_run_callback(): scsi_bus_resume+0x0/0x40 returns -5
[  249.015596] PM: Device 1:0:0:0 failed to resume async: error -5
[  252.014971] 
[  252.014972] floppy driver state
[  252.014974] -------------------
[  252.014999] now=4294919360 last interrupt=4294667995 diff=251365 last called handler=reset_interrupt [floppy]
[  252.015001] timeout_message=lock fdc
[  252.015002] last output bytes:
[  252.015004]  8 80 4294667982
[  252.015006]  8 80 4294667982
[  252.015007]  8 80 4294667983
[  252.015009]  8 80 4294667993
[  252.015010]  8 80 4294667993
[  252.015012]  8 80 4294667993
[  252.015013]  8 80 4294667994
[  252.015015]  e 80 4294667994
[  252.015016] 13 80 4294667994
[  252.015018]  0 90 4294667994
[  252.015019] 1a 90 4294667994
[  252.015020]  0 90 4294667994
[  252.015022] 12 90 4294667994
[  252.015023]  0 90 4294667994
[  252.015025] 14 90 4294667994
[  252.015026] 18 80 4294667995
[  252.015028]  8 80 4294667995
[  252.015029]  8 80 4294667995
[  252.015031]  8 80 4294667995
[  252.015032]  8 80 4294667996
[  252.015033] last result at 4294667996
[  252.015035] last redo_fd_request at 4294667996
[  252.015046] status=0
[  252.015047] fdc_busy=1
[  252.015056] do_floppy=reset_interrupt [floppy]
[  252.015058] cont=ffffffffa0008380
[  252.015060] current_req=          (null)
[  252.015061] command_status=-1
[  252.015061] 
[  252.015065] floppy0: floppy timeout called
[  252.015212] PM: resume of devices complete after 63177.760 msecs
[  252.016193] PM: Finishing wakeup.
[  252.016295] pci 0000:00:00.0: no hotplug settings from platform
[  252.016307] pci 0000:00:00.0: using default PCI settings
[  252.016326] pci 0000:00:01.0: no hotplug settings from platform
[  252.016331] pci 0000:00:01.0: using default PCI settings
[  252.016343] nForce2_smbus 0000:00:01.1: no hotplug settings from platform
[  252.016348] nForce2_smbus 0000:00:01.1: using default PCI settings
[  252.016359] pci 0000:00:01.2: no hotplug settings from platform
[  252.016364] pci 0000:00:01.2: using default PCI settings
[  252.016375] ohci-pci 0000:00:02.0: no hotplug settings from platform
[  252.016380] ohci-pci 0000:00:02.0: using default PCI settings
[  252.016391] ehci-pci 0000:00:02.1: no hotplug settings from platform
[  252.016395] ehci-pci 0000:00:02.1: using default PCI settings
[  252.016407] pci 0000:00:04.0: no hotplug settings from platform
[  252.016411] pci 0000:00:04.0: using default PCI settings
[  252.016428] 8139too 0000:01:06.0: no hotplug settings from platform
[  252.016433] 8139too 0000:01:06.0: using default PCI settings
[  252.016438] sd 1:0:0:0: [sdb] Unhandled error code
[  252.016447] pata_amd 0000:00:06.0: no hotplug settings from platform
[  252.016452] pata_amd 0000:00:06.0: using default PCI settings
[  252.016461] sd 1:0:0:0: [sdb]  
[  252.016463] sata_nv 0000:00:08.0: no hotplug settings from platform
[  252.016468] sata_nv 0000:00:08.0: using default PCI settings
[  252.016475] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[  252.016479] pcieport 0000:00:09.0: no hotplug settings from platform
[  252.016485] sd 1:0:0:0: [sdb] CDB: 
[  252.016197] Restarting tasks ... 
[  252.016489] Write(10)<4>[  252.016493] nvidia 0000:02:00.0: no hotplug settings from platform
[  252.016500] pcieport 0000:00:0c.0: no hotplug settings from platform
[  252.016497] : 2a 00 0d d2 a8 00 00 00 08 00
[  252.016521] end_request: I/O error, dev sdb, sector 231909376
[  252.016523] pci 0000:03:00.0: no hotplug settings from platform
[  252.016535] snd_virtuoso 0000:04:04.0: no hotplug settings from platform
[  252.016538] snd_virtuoso 0000:04:04.0: using default PCI settings
[  252.016556] pci 0000:00:18.0: no hotplug settings from platform
[  252.016559] pci 0000:00:18.0: using default PCI settings
[  252.016567] pci 0000:00:18.1: no hotplug settings from platform
[  252.016569] pci 0000:00:18.1: using default PCI settings
[  252.016577] pci 0000:00:18.2: no hotplug settings from platform
[  252.016579] pci 0000:00:18.2: using default PCI settings
[  252.016587] pci 0000:00:18.3: no hotplug settings from platform
[  252.016589] pci 0000:00:18.3: using default PCI settings
[  252.016597] pci 0000:00:18.4: no hotplug settings from platform
[  252.016602] pci 0000:00:18.4: using default PCI settings
[  252.016629] EXT4-fs warning (device sdb2): ext4_end_bio:317: I/O error -5 writing to inode 7213541 (offset 0 size 0 starting block 28988673)
[  252.016636] Buffer I/O error on device sdb2, logical block 28988416
[  252.017190] sd 1:0:0:0: [sdb] Unhandled error code
[  252.017196] sd 1:0:0:0: [sdb]  
[  252.017200] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[  252.017205] sd 1:0:0:0: [sdb] CDB: 
[  252.017207] Write(10): 2a 00 0d d2 a8 38 00 00 08 00
[  252.017222] end_request: I/O error, dev sdb, sector 231909432
[  252.017297] EXT4-fs warning (device sdb2): ext4_end_bio:317: I/O error -5 writing to inode 7213541 (offset 0 size 0 starting block 28988680)
[  252.017303] Buffer I/O error on device sdb2, logical block 28988423
[  252.017386] sd 1:0:0:0: [sdb] Unhandled error code
[  252.017391] sd 1:0:0:0: [sdb]  
[  252.017394] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[  252.017399] sd 1:0:0:0: [sdb] CDB: 
[  252.017401] Write(10): 2a 00 00 06 7b 00 00 00 80 00
[  252.017415] end_request: I/O error, dev sdb, sector 424704
[  252.017488] EXT4-fs warning (device sdb2): ext4_end_bio:317: I/O error -5 writing to inode 7346665 (offset 0 size 0 starting block 53104)
[  252.017493] Buffer I/O error on device sdb2, logical block 52832
[  252.017574] Buffer I/O error on device sdb2, logical block 52833
[  252.017645] Buffer I/O error on device sdb2, logical block 52834
[  252.017715] Buffer I/O error on device sdb2, logical block 52835
[  252.017785] Buffer I/O error on device sdb2, logical block 52836
[  252.017855] Buffer I/O error on device sdb2, logical block 52837
[  252.017935] Buffer I/O error on device sdb2, logical block 52838
[  252.018006] Buffer I/O error on device sdb2, logical block 52839
[  252.025574] done.
[  252.028938] sd 1:0:0:0: [sdb] Unhandled error code
[  252.028942] sd 1:0:0:0: [sdb]  
[  252.028944] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[  252.028946] sd 1:0:0:0: [sdb] CDB: 
[  252.028948] Write(10): 2a 00 0d d2 a9 80 00 00 10 00
[  252.028954] end_request: I/O error, dev sdb, sector 231909760
[  252.028958] EXT4-fs warning (device sdb2): ext4_end_bio:317: I/O error -5 writing to inode 7471524 (offset 0 size 8192 starting block 28988722)
[  252.030846] sd 1:0:0:0: [sdb] Unhandled error code
[  252.030849] sd 1:0:0:0: [sdb]  
[  252.030851] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[  252.030853] sd 1:0:0:0: [sdb] CDB: 
[  252.030854] Write(10): 2a 00 0d d2 a9 90 00 00 18 00
[  252.030860] end_request: I/O error, dev sdb, sector 231909776
[  252.030864] EXT4-fs warning (device sdb2): ext4_end_bio:317: I/O error -5 writing to inode 7476558 (offset 0 size 12288 starting block 28988725)
[  257.659457] sd 1:0:0:0: [sdb] Unhandled error code
[  257.659471] sd 1:0:0:0: [sdb]  
[  257.659477] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[  257.659483] sd 1:0:0:0: [sdb] CDB: 
[  257.659486] Write(10): 2a 00 08 84 27 18 00 00 68 00
[  257.659504] end_request: I/O error, dev sdb, sector 142878488
[  257.659541] Aborting journal on device sdb2-8.
[  257.659585] sd 1:0:0:0: [sdb] Unhandled error code
[  257.659587] sd 1:0:0:0: [sdb]  
[  257.659589] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[  257.659591] sd 1:0:0:0: [sdb] CDB: 
[  257.659592] Write(10): 2a 00 08 84 08 00 00 00 08 00
[  257.659598] end_request: I/O error, dev sdb, sector 142870528
[  257.659601] Buffer I/O error on device sdb2, logical block 17858560
[  257.659603] lost page write due to I/O error on sdb2
[  257.659622] JBD2: Error -5 detected when updating journal superblock for sdb2-8.

I'm using Ubuntu Studio 14.04, and the computer is a desktop box. Has anyone encountered a similar issue before? I (used to) use suspend/resume several times a day, so this is a royal pain and any help would be much appreciated.

---

### Post by ajgreeny on 2014-11-15
There seem to be two main things causing delays, the first being at:-
```
[  189.380214] sd 0:0:0:0: [sda] Starting disk
[  194.382858] ata2: link is slow to respond, please be patient (ready=0)
[  198.918956] ata2: SRST failed (errno=-16)
[  204.418429] ata2: link is slow to respond, please be patient (ready=0)
[  208.954526] ata2: SRST failed (errno=-16)
[  214.454003] ata2: link is slow to respond, please be patient (ready=0)
[  243.964078] ata2: SRST failed (errno=-16)
[  243.964082] ata2: limiting SATA link speed to 1.5 Gbps
[  249.004858] ata2: SRST failed (errno=-16)
[  249.015450] ata2: reset failed, giving up
[  249.015454] ata2.00: disabled
```
which from your description, and if it all relates to sda, sounds as if it's the SSD, not the new HDD sdb.

The problem with sdb appears later at:-
```
[  252.030860] end_request: I/O error, dev sdb, sector 231909776
[  252.030864] EXT4-fs warning (device sdb2): ext4_end_bio:317: I/O  error -5 writing to inode 7476558 (offset 0 size 12288 starting block  28988725)
[  257.659457] sd 1:0:0:0: [sdb] Unhandled error code
```
I am afraid I don't have much top offer in regard to solutions but show these two places with delays which can perhaps use for more detailed searches.

Sorry if you had already realised these two delay points were there, but you did not give any indication of what you had figured out so far.

---

### Post by vonbureck on 2014-11-15
Thanks for your reply, I've double-checked that the Seagate on sdb must somehow be causing the problem - I swapped it back for the old Hitachi HDD (also hosting /home, same filesystem and everything) and there were no resume errors at all.

Another thing: I booted from the Ubuntu live DVD, mounted the Seagate, suspended the system and got the same resume problem (i.e. the Seagate was not available after resume). Also, the network interface (eth0) in the resumed live booted system wouldn't come back up.

My only idea is that the Seagate has some special sleep/resume parameter that needs to be set somewhere, but no luck with googling it so far.

---

