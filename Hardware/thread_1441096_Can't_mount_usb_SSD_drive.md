---
title: "Can't mount usb SSD drive"
date: 2010-03-28
forum: Hardware
---

### Post by gsch on 2010-03-28
First, a bit of background: My Acer travelmate 2450 has an IDE harddrive which I decided to replace with an external usb Kingston SSD drive. I cloned the IDE drive to the new SSD. I decided to remove the native IDE drive since I could not get into the BIOS to change the boot sequence to USB first. Started up the computer with only the usb drive attached and it worked beautifully for a week since I always plugged the drive into the same USB bus. Footnote: I'm still on Jaunty, Karmic would not boot up for me.
 
Then I moved the drive to a different usb bus before startup and the system does not boot up anymore, even when attached to the original usb bus. Says "operating system not found". Popped in a live cd, but can't mount the SSD drive. Booted up with the old IDE drive and still can't mount the SSD drive. Here's what I see with fdisk -l
 
sudo fdisk -l
 
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xce6fd1bc
 
Device Boot Start End Blocks Id System
/dev/sda1 * 1 1824 14651248+ 83 Linux
/dev/sda2 1825 7296 43953840 5 Extended
/dev/sda5 7134 7296 1309266 82 Linux swap / Solaris
/dev/sda6 1825 7133 42644479+ 83 Linux
Partition table entries are not in disk order
 
I did not expect an sda6. I only created additional /home and swap-partitions.
 
This is the output of lsusb, seems like it sees the SSD drive (Initio Corp?):
 
lsusb
Bus 001 Device 003: ID 13fd:1840 Initio Corporation 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 
After booting up with the old IDE and doing ls -lrt /dev/disk/by-id:
 
total 0
lrwxrwxrwx 1 root root 9 2010-03-28 16:04 ata-HTS541060G9AT00_MP27MBXDG62DYH -> ../../sda
lrwxrwxrwx 1 root root 10 2010-03-28 16:04 ata-HTS541060G9AT00_MP27MBXDG62DYH-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2010-03-28 16:04 ata-HTS541060G9AT00_MP27MBXDG62DYH-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2010-03-28 16:04 ata-HTS541060G9AT00_MP27MBXDG62DYH-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 2010-03-28 16:04 ata-HTS541060G9AT00_MP27MBXDG62DYH-part6 -> ../../sda6
lrwxrwxrwx 1 root root 9 2010-03-28 16:05 scsi-SATA_HTS541060G9AT00_MP27MBXDG62DYH -> ../../sda
lrwxrwxrwx 1 root root 10 2010-03-28 16:05 scsi-SATA_HTS541060G9AT00_MP27MBXDG62DYH-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2010-03-28 16:05 scsi-SATA_HTS541060G9AT00_MP27MBXDG62DYH-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2010-03-28 16:05 scsi-SATA_HTS541060G9AT00_MP27MBXDG62DYH-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 2010-03-28 16:05 scsi-SATA_HTS541060G9AT00_MP27MBXDG62DYH-part6 -> ../../sda6
 
Seems like the IDE and SSD have precisely the same names (because it's cloned?). Is it path-confusion that lies at the root of my problems?
 
When doing ls -lrt /dev/disk/by-path:
total 0
lrwxrwxrwx 1 root root 9 2010-03-28 16:04 pci-0000:00:14.1-scsi-0:0:0:0 -> ../../sda
lrwxrwxrwx 1 root root 9 2010-03-28 16:04 pci-0000:00:14.1-scsi-0:0:1:0 -> ../../sr0
lrwxrwxrwx 1 root root 10 2010-03-28 16:04 pci-0000:00:14.1-scsi-0:0:0:0-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2010-03-28 16:04 pci-0000:00:14.1-scsi-0:0:0:0-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2010-03-28 16:04 pci-0000:00:14.1-scsi-0:0:0:0-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 2010-03-28 16:04 pci-0000:00:14.1-scsi-0:0:0:0-part6 -> ../../sda6
 
 
sr0 is the CD rom, I think
 
When doing ls -lrt /dev/disk/by-uuid:
total 0
lrwxrwxrwx 1 root root 10 2010-03-28 16:04 ad821843-7d63-44d5-91f9-7a125ac7d2db -> ../../sda1
lrwxrwxrwx 1 root root 10 2010-03-28 16:04 c51a9408-3052-45ed-b086-0b844a6b9cb3 -> ../../sda5
lrwxrwxrwx 1 root root 10 2010-03-28 16:04 f93cd169-9fe1-42aa-ae4b-be9888f92b7d -> ../../sda6
 
These are the partitions of the IDE drive? (I have a home- and swap-partition).
 
I guess I won't be able to boot from the SSD again if I can't even mount it. Can you help?

---

### Post by gsch on 2010-03-29
Some more info: My flash disk mounts automatically on the same usb port.
 
Any Guru out there that has an idea on how to tackle the problem?

---

### Post by gsch on 2010-03-30
bump
 
A dragon too scary for the community?

---

### Post by gsch on 2010-03-30
bump

---

### Post by gsch on 2010-04-01
bump

---

### Post by dabl on 2010-04-01
OK, I'll bite.

First -- the fundamentals of USB. From the perspective of the default OS, hot-pluggable USB devices are inherently ID-less.  In other words, they are just the "next guy on the bus" -- they get a new "temporary" ID assigned every time they show up.  That's great for mice and cameras, not so great for bootable disk drives.

Second -- the fundamentals of bootable drives.  You need a boot routine of some kind on the MBR of the boot sector (grub, normally) and it needs to be marked with the "boot" flag for some BIOSs to see.

Third -- BIOS.  The "boot from USB" option needs to be enabled, and then the problem becomes the inability to make a hot-plugged device permanently the first device in sequence to be booted.  So, you may be stuck entering BIOS every time you want to boot the USB drive, and move it to the top of the bootable device list, and then proceed with startup.

If you intended to leave the SSD connected full time, you could set up /etc/fstab to boot it "by-UUID", using its UUID number.

Any useful hints there?

---

### Post by gsch on 2010-04-01
Thanks. I'll run with that info this weekend and see if I can save this sucker. I appreciate you showing me the path.

I'll be back ...

---

### Post by gsch on 2010-04-02
This reply is not a request for help (just yet!), but only a documentation of my thoughts about the problem in the context of what you said. Feel free to comment.

1. I am unable to get a UUID for the usb SSD, which makes it impossible to access the device, even with the dd command (with confidence that i actually does something). dmesg says that the SSD has and sdb-drive letter, but also reports errors (I/O error in sector 0, another error in sector 24). Not being able to influence the SSD by using the dd command with /dev/sdb makes me think that it is futile to try and use command line. I cannot even format the drive.

Linux, Windows, and a drive cloning tool all see the device and the cloning tool even knows how large it is, but none of these can access it. This reinforces the idea that there is no command line solution.

2. I suspect that the SSD itself has not changed or been damaged (i.e. the sectors 0 and 24 errors), since the problem started when I changed to a different USB port (that should not influence the integrity of the SSD!?). This makes me think that the BIOS got confused when I changed USB ports, and I have to get into the BIOS somehow. HOWEVER, I did try to boot from the "second hard drive" from a rescue CD (ultimate boot CD) and was told that the MBR cannot be read. The first reaction to this message is to go back to point #1 above and try and repair the MBR in some way. Futile.

3. General conclusion: forget the command line, get into the BIOS in some way.

---

### Post by PatrickVogeli on 2010-04-02
I don't know about your problem, but are you sure what you are doing is a good idea? I'm quite sure an SSD usb disk will be slower than the Ide drive you had..

---

### Post by gsch on 2010-04-02
An SSD's characteristics are besides the point here. I'm sure there are other threads where you can discuss that. I can assure you that it was faster, quieter and cooler (temperature). I'll never go back to traditional hard drives.

---

### Post by logonna on 2010-04-02
Almost the same problem 

Kingston V+ SSD 128g in its USB box and i can't mount it 
dmesg : 

[46287.149853] Initializing USB Mass Storage driver...                                                                                                                              
[46287.150504] scsi6 : SCSI emulation for USB Mass Storage devices                                                                                                                  
[46287.152104] usb-storage: device found at 4                                                                                                                                       
[46287.152112] usb-storage: waiting for device to settle before scanning                                                                                                            
[46287.152131] usbcore: registered new interface driver usb-storage                                                                                                                 
[46287.152139] USB Mass Storage support registered.                                                                                                                                 
[46292.153368] usb-storage: device scan complete                                                                                                                                    
[46292.154900] scsi 6:0:0:0: Direct-Access     PI-291   FCR-HS2SATA      1.04 PQ: 0 ANSI: 4                                                                                         
[46292.156273] sd 6:0:0:0: Attached scsi generic sg2 type 0                                                                                                                         
[46292.170794] sd 6:0:0:0: [sdb] 250069680 512-byte logical blocks: (128 GB/119 GiB)                                                                                                
[46292.176456] sd 6:0:0:0: [sdb] Write Protect is off                                                                                                                               
[46292.176463] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00                                                                                                                            
[46292.176466] sd 6:0:0:0: [sdb] Assuming drive cache: write through                                                                                                                
[46292.178555] sd 6:0:0:0: [sdb] Assuming drive cache: write through                                                                                                                
[46292.178565]  sdb:                                                                                                                                                                
[46292.179601] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE                                                                                                    
[46292.179608] sd 6:0:0:0: [sdb] Sense Key : Illegal Request [current]                                                                                                              
[46292.179614] Info fld=0x0                                                                                                                                                         
[46292.179616] sd 6:0:0:0: [sdb] Add. Sense: Logical block address out of range                                                                                                     
[46292.179623] end_request: I/O error, dev sdb, sector 0                                                                                                                            
[46292.179629] Buffer I/O error on device sdb, logical block 0                                                                                                                      
[46292.181460] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE                                                                                                    
[46292.181471] sd 6:0:0:0: [sdb] Sense Key : Illegal Request [current]                                                                                                              
[46292.181481] Info fld=0x0                                                                                                                                                         
[46292.181485] sd 6:0:0:0: [sdb] Add. Sense: Logical block address out of range                                                                                                     
[46292.181495] end_request: I/O error, dev sdb, sector 0                                                                                                                            
[46292.181505] Buffer I/O error on device sdb, logical block 0                                                                                                                      
[46292.182588] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE                                                                                                    
[46292.182598] sd 6:0:0:0: [sdb] Sense Key : Illegal Request [current]                                                                                                              
[46292.182607] Info fld=0x0                                                                                                                                                         
[46292.182611] sd 6:0:0:0: [sdb] Add. Sense: Logical block address out of range                                                                                                     
[46292.182621] end_request: I/O error, dev sdb, sector 0                                                                                                                            
[46292.182628] Buffer I/O error on device sdb, logical block 0                                                                                                                      
[46292.183456] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE                                                                                                    
[46292.183463] sd 6:0:0:0: [sdb] Sense Key : Illegal Request [current]                                                                                                              
[46292.183471] Info fld=0x0                                                                                                                                                         
[46292.183475] sd 6:0:0:0: [sdb] Add. Sense: Logical block address out of range                                                                                                     
[46292.183485] end_request: I/O error, dev sdb, sector 0                                                                                                                            
[46292.183491] Buffer I/O error on device sdb, logical block 0                                                                                                                      
[46292.184331] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE                                                                                                    
[46292.184338] sd 6:0:0:0: [sdb] Sense Key : Illegal Request [current]                                                                                                              
[46292.184346] Info fld=0x0                                                                                                                                                         
[46292.184349] sd 6:0:0:0: [sdb] Add. Sense: Logical block address out of range                                                                                                     
[46292.184360] end_request: I/O error, dev sdb, sector 0                                                                                                                            
[46292.184366] Buffer I/O error on device sdb, logical block 0                                                                                                                      
[46292.184378] ldm_validate_partition_table(): Disk read failed.                                                                                                                    
[46292.185208] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE                                                                                                    
[46292.185215] sd 6:0:0:0: [sdb] Sense Key : Illegal Request [current]                                                                                                              
[46292.185222] Info fld=0x0                                                                                                                                                         
[46292.185226] sd 6:0:0:0: [sdb] Add. Sense: Logical block address out of range                                                                                                     
[46292.185237] end_request: I/O error, dev sdb, sector 0                                                                                                                            
[46292.185243] Buffer I/O error on device sdb, logical block 0                                                                                                                      
[46292.186082] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE                                                                                                    
[46292.186086] sd 6:0:0:0: [sdb] Sense Key : Illegal Request [current]                                                                                                              
[46292.186090] Info fld=0x0                                                                                                                                                         
[46292.186092] sd 6:0:0:0: [sdb] Add. Sense: Logical block address out of range                                                                                                     
[46292.186098] end_request: I/O error, dev sdb, sector 0                                                                                                                            
[46292.186101] Buffer I/O error on device sdb, logical block 0                                                                                                                      
[46292.187476] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE                                                                                                    
[46292.187484] sd 6:0:0:0: [sdb] Sense Key : Illegal Request [current]                                                                                                              
[46292.187490] Info fld=0x0                                                                                                                                                         
[46292.187493] sd 6:0:0:0: [sdb] Add. Sense: Logical block address out of range                                                                                                     
[46292.187499] end_request: I/O error, dev sdb, sector 0                                                                                                                            
[46292.187505] Buffer I/O error on device sdb, logical block 0                                                                                                                      
[46292.188469] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE                                                                                                    
[46292.188475] sd 6:0:0:0: [sdb] Sense Key : Illegal Request [current]                                                                                                              
[46292.188480] Info fld=0x0                                                                                                                                                         
[46292.188482] sd 6:0:0:0: [sdb] Add. Sense: Logical block address out of range                                                                                                     
[46292.188488] end_request: I/O error, dev sdb, sector 0                                                                                                                            
[46292.188493] Buffer I/O error on device sdb, logical block 0                                                                                                                      
[46292.188508] Dev sdb: unable to read RDB block 0                                                                                                                                  
[46292.192497] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE                                                                                                    
[46292.192505] sd 6:0:0:0: [sdb] Sense Key : Illegal Request [current]                                                                                                              
[46292.192511] Info fld=0x0                                                                                                                                                         
[46292.192513] sd 6:0:0:0: [sdb] Add. Sense: Logical block address out of range                                                                                                     
[46292.192520] end_request: I/O error, dev sdb, sector 0                                                                                                                            
[46292.192527] Buffer I/O error on device sdb, logical block 0                                                                                                                      
[46292.195231] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE                                                                                                    
[46292.195239] sd 6:0:0:0: [sdb] Sense Key : Illegal Request [current]                                                                                                              
[46292.195246] Info fld=0x0                                                                                                                                                         
[46292.195248] sd 6:0:0:0: [sdb] Add. Sense: Logical block address out of range                                                                                                     
[46292.195254] end_request: I/O error, dev sdb, sector 0                                                                                                                            
[46412.521743] psmouse.c: TouchPad at isa0060/serio1/input0 lost synchronization, throwing 4 bytes away.                                                                            
[46413.035927] psmouse.c: resync failed, issuing reconnect request                                                                                                                  
[46440.621124] INFO: task async/0:4978 blocked for more than 120 seconds.                                                                                                           
[46440.621133] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.                                                                                            
[46440.621141] async/0       D c08185c0     0  4978      2 0x00000000                                                                                                               
[46440.621154]  f539bd4c 00000046 f32b0000 c08185c0 f3ce4168 c08185c0 3ddba7ab 00002a1a                                                                                             
[46440.621173]  c08185c0 c08185c0 f3ce4168 c08185c0 00000001 00002a1a c08185c0 f51a6700                                                                                             
[46440.621191]  f3ce3ed0 c20635c0 00000002 f539bd94 f539bd58 c05720be f539bd8c f539bd60                                                                                             
[46440.621209] Call Trace:                                                                                                                                                          
[46440.621226]  [<c05720be>] io_schedule+0x1e/0x30                                                                                                                                  
[46440.621236]  [<c01b2dd5>] sync_page+0x35/0x40                                                                                                                                    
[46440.621245]  [<c05725f7>] __wait_on_bit_lock+0x47/0x90                                                                                                                           
[46440.621254]  [<c01b2da0>] ? sync_page+0x0/0x40                                                                                                                                   
[46440.621266]  [<c020f5f0>] ? blkdev_readpage+0x0/0x20                                                                                                                             
[46440.621274]  [<c01b2d89>] __lock_page+0x79/0x80                                                                                                                                  
[46440.621285]  [<c015c1c0>] ? wake_bit_function+0x0/0x50                                                                                                                           
[46440.621294]  [<c01b467f>] read_cache_page_async+0xbf/0xd0                                                                                                                        
[46440.621304]  [<c01b46a2>] read_cache_page+0x12/0x60                                                                                                                              
[46440.621314]  [<c023301a>] read_dev_sector+0x3a/0x80                                                                                                                              
[46440.621324]  [<c02385a0>] ? ultrix_partition+0x0/0xe0                                                                                                                            
[46440.621333]  [<c02385c5>] ultrix_partition+0x25/0xe0                                                                                                                             
[46440.621343]  [<c02385a0>] ? ultrix_partition+0x0/0xe0                                                                                                                            
[46440.621352]  [<c023372e>] check_partition+0x10e/0x180                                                                                                                            
[46440.621363]  [<c0233846>] rescan_partitions+0xa6/0x330                                                                                                                           
[46440.621374]  [<c0316092>] ? kobject_get+0x12/0x20                                                                                                                                
[46440.621383]  [<c0316092>] ? kobject_get+0x12/0x20                                                                                                                                
[46440.621394]  [<c03a3513>] ? get_device+0x13/0x20                                                                                                                                 
[46440.621404]  [<c03c5eef>] ? sd_open+0x5f/0x1b0                                                                                                                                   
[46440.621413]  [<c0210000>] __blkdev_get+0x140/0x310                                                                                                                               
[46440.621423]  [<c020f30c>] ? bdget+0xec/0x100                                                                                                                                     
[46440.621432]  [<c02101da>] blkdev_get+0xa/0x10                                                                                                                                    
[46440.621441]  [<c0233180>] register_disk+0x120/0x140                                                                                                                              
[46440.621452]  [<c030c76d>] ? blk_register_region+0x2d/0x40                                                                                                                        
[46440.621462]  [<c030c110>] ? exact_match+0x0/0x10                                                                                                                                 
[46440.621471]  [<c030c910>] add_disk+0x80/0x140                                                                                                                                    
[46440.621480]  [<c030c110>] ? exact_match+0x0/0x10                                                                                                                                 
[46440.621488]  [<c030c480>] ? exact_lock+0x0/0x20                                                                                                                                  
[46440.621499]  [<c03c8c8f>] sd_probe_async+0xff/0x1c0                                                                                                                              
[46440.621509]  [<c0127b68>] ? default_spin_lock_flags+0x8/0x10                                                                                                                     
[46440.621519]  [<c0573bda>] ? _spin_lock_irqsave+0x2a/0x40                                                                                                                         
[46440.621529]  [<c0162a75>] run_one_entry+0x65/0x190                                                                                                                               
[46440.621538]  [<c0127b68>] ? default_spin_lock_flags+0x8/0x10                                                                                                                     
[46440.621547]  [<c0573bda>] ? _spin_lock_irqsave+0x2a/0x40                                                                                                                         
[46440.621557]  [<c015c4ab>] ? add_wait_queue+0x3b/0x50                                                                                                                             
[46440.621566]  [<c0162ba0>] ? async_thread+0x0/0xd0                                                                                                                                
[46440.621575]  [<c0162bed>] async_thread+0x4d/0xd0                                                                                                                                 
[46440.621585]  [<c013c4c0>] ? default_wake_function+0x0/0x10                                                                                                                       
[46440.621594]  [<c015be8c>] kthread+0x7c/0x90                                                                                                                                      
[46440.621602]  [<c015be10>] ? kthread+0x0/0x90                                                                                                                                     
[46440.621612]  [<c0104047>] kernel_thread_helper+0x7/0x10                                                                                                                          
[46472.201704] sd 6:0:0:0: timing out command, waited 180s                                                                                                                          
[46472.201724] sd 6:0:0:0: [sdb] Unhandled sense code                                                                                                                               
[46472.201730] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE                                                                                                    
[46472.201740] sd 6:0:0:0: [sdb] Sense Key : Hardware Error [current]                                                                                                               
[46472.201752] Info fld=0x0                                                                                                                                                         
[46472.201757] sd 6:0:0:0: [sdb] Add. Sense: Internal target failure                                                                                                                
[46472.201770] end_request: I/O error, dev sdb, sector 24                                                                                                                           
[46472.201779] __ratelimit: 1 callbacks suppressed                                                                                                                                  
[46472.201785] Buffer I/O error on device sdb, logical block 3                                                                                                                      
[46652.205037] sd 6:0:0:0: timing out command, waited 180s                                                                                                                          
[46652.205057] sd 6:0:0:0: [sdb] Unhandled sense code                                                                                                                               
[46652.205064] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE                                                                                                    
[46652.205073] sd 6:0:0:0: [sdb] Sense Key : Hardware Error [current]                                                                                                               
[46652.205085] Info fld=0x0                                                                                                                                                         
[46652.205090] sd 6:0:0:0: [sdb] Add. Sense: Internal target failure                                                                                                                
[46652.205104] end_request: I/O error, dev sdb, sector 24                                                                                                                           
[46652.205113] Buffer I/O error on device sdb, logical block 3                                                                                                                      
[46652.206152] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE                                                                                                    
[46652.206162] sd 6:0:0:0: [sdb] Sense Key : Illegal Request [current]                                                                                                              
[46652.206173] Info fld=0x0                                                                                                                                                         
[46652.206177] sd 6:0:0:0: [sdb] Add. Sense: Logical block address out of range
[46652.206190] end_request: I/O error, dev sdb, sector 0
[46652.206198] Buffer I/O error on device sdb, logical block 0
[46652.207152] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[46652.207161] sd 6:0:0:0: [sdb] Sense Key : Illegal Request [current]
[46652.207172] Info fld=0x0
[46652.207176] sd 6:0:0:0: [sdb] Add. Sense: Logical block address out of range
[46652.207189] end_request: I/O error, dev sdb, sector 0
[46652.207196] Buffer I/O error on device sdb, logical block 0
[46652.207233]  unable to read partition table
[46652.214302] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[46652.214315] sd 6:0:0:0: [sdb] Attached SCSI disk
[46652.229289] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[46652.229302] sd 6:0:0:0: [sdb] Sense Key : Illegal Request [current]
[46652.229314] Info fld=0x0
[46652.229319] sd 6:0:0:0: [sdb] Add. Sense: Logical block address out of range
[46652.229333] end_request: I/O error, dev sdb, sector 0
[46652.229343] Buffer I/O error on device sdb, logical block 0
[46832.237113] sd 6:0:0:0: timing out command, waited 180s
[46832.237138] sd 6:0:0:0: [sdb] Unhandled sense code
[46832.237144] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[46832.237154] sd 6:0:0:0: [sdb] Sense Key : Hardware Error [current]
[46832.237166] Info fld=0x0
[46832.237171] sd 6:0:0:0: [sdb] Add. Sense: Internal target failure
[46832.237184] end_request: I/O error, dev sdb, sector 8
[46832.237193] Buffer I/O error on device sdb, logical block 1
[46832.237203] Buffer I/O error on device sdb, logical block 2
[46832.237210] Buffer I/O error on device sdb, logical block 3
[46832.237218] Buffer I/O error on device sdb, logical block 4
[46832.237225] Buffer I/O error on device sdb, logical block 5
[46832.237233] Buffer I/O error on device sdb, logical block 6
[46832.237240] Buffer I/O error on device sdb, logical block 7
[46832.237247] Buffer I/O error on device sdb, logical block 8
[46832.237255] Buffer I/O error on device sdb, logical block 9
[46832.237262] Buffer I/O error on device sdb, logical block 10
[46832.238236] sd 6:0:0:0: timing out command, waited 180s
[46832.238247] sd 6:0:0:0: [sdb] Unhandled sense code
[46832.238252] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[46832.238261] sd 6:0:0:0: [sdb] Sense Key : Hardware Error [current]
[46832.238271] Info fld=0x0
[46832.238276] sd 6:0:0:0: [sdb] Add. Sense: Internal target failure
[46832.238288] end_request: I/O error, dev sdb, sector 248
[46832.239237] sd 6:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[46832.239246] sd 6:0:0:0: [sdb] Sense Key : Illegal Request [current]
[46832.239257] Info fld=0x0
[46832.239262] sd 6:0:0:0: [sdb] Add. Sense: Logical block address out of range
[46832.239274] end_request: I/O error, dev sdb, sector 0

---

### Post by gsch on 2010-04-03
Thanks for the post logonna. My dmesg says that there are problems in sectors 0 and 24, and also says that the partition can't be read.

I have now exhausted all possible paths to save my SSD. It is simply corrupt and can't be read or edited with Linux, Windows, LiveCD or a variety of rescue disks. The problem did NOT lie with the USB power supply as some forums suggest. _The SSD has a 3 year warranty, and I will claim a replacement this coming week._

I found one forum which pointed to a jaunty kernel for 64 bit systems, but I have a 32 bit system. Anyways, to install a different kernel, access to the disk is necessary.

I have learnt a lot about my linux system from this experience. Mostly that dmesg | tail is and excellent diagnostic tool for USB devices.

Good luck to others who experienced the same problem. Please make yourselves heard on the forums, it may be a product quality or incompatibility problem. SSDs are quite new and we have to highlight these problems for the sake of more stable systems in the future. I'll install Lucid Lynx on my new SSD, just in case it is a kernel thing.

---

### Post by HugoCanada1 on 2010-09-22
Similar Problem here : Using Kingston V series 128go and Acomdata Samurai USB3 or using generic usb enclosure.
 
Cannot use Ghostzilla to ghost an hard drive and put image on usb external SSD. 
 
I can mount the drive, but when ghosting there is write data block error message. 
 
But no problem when using the SSD with on-motherboard sata without the external enclosure.

---

