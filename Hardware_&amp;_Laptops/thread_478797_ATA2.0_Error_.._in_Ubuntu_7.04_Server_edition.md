---
title: "ATA2.0 Error .. in Ubuntu 7.04 Server edition"
date: 2007-06-19
forum: Hardware &amp; Laptops
---

### Post by MR.GIL on 2007-06-19
Mainboard : MSI - K7N2 Delta-L/ ILSR  

 Two sata disk (ATA Maxtor 6Y120M0 120GB) (ATA SAMSUNG SP2504C 250GB)

> Jun 19 00:55:10 AMBERT kernel: [   30.818755] NFORCE2: IDE controller at PCI slot 0000:00:09.0                                                                                                                   
Jun 19 00:55:10 AMBERT kernel: [   30.818771] NFORCE2: chipset revision 162                                                                                                                                      
Jun 19 00:55:10 AMBERT kernel: [   30.818774] NFORCE2: not 100%% native mode: will probe irqs later                                                                                                              
Jun 19 00:55:10 AMBERT kernel: [   30.818779] NFORCE2: BIOS didn't set cable bits correctly. Enabling workaround.                                                                                                
Jun 19 00:55:10 AMBERT kernel: [   30.818782] NFORCE2: BIOS didn't set cable bits correctly. Enabling workaround.                                                                                                
Jun 19 00:55:10 AMBERT kernel: [   30.818788] NFORCE2: 0000:00:09.0 (rev a2) UDMA133 controller                                                                                                                  
Jun 19 00:55:10 AMBERT kernel: [   30.818794] NFORCE2: port 0x01f0 already claimed by ide0                                                                                                                       
Jun 19 00:55:10 AMBERT kernel: [   30.818844] NFORCE2: port 0x0170 already claimed by ide1                                                                                                                       
Jun 19 00:55:10 AMBERT kernel: [   30.818889] NFORCE2: neither IDE port enabled (BIOS)                                                                                                                           
Jun 19 00:55:10 AMBERT kernel: [   30.826377] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)                                                                                                             
Jun 19 00:55:10 AMBERT kernel: [   30.826752] sata_promise 0000:01:0b.0: version 2.01                                                                                                                            
Jun 19 00:55:10 AMBERT kernel: [   30.826792] sata_promise PATA port found                                                                                                                                       
Jun 19 00:55:10 AMBERT kernel: [   30.852514] ata1: SATA max UDMA/133 cmd 0xf88a4200 ctl 0xf88a4238 bmdma 0x00000000 irq 11                                                                                      
Jun 19 00:55:10 AMBERT kernel: [   30.853738] ata2: SATA max UDMA/133 cmd 0xf88a4280 ctl 0xf88a42b8 bmdma 0x00000000 irq 11                                                                                      
Jun 19 00:55:10 AMBERT kernel: [   30.853774] ata3: PATA max UDMA/133 cmd 0xf88a4300 ctl 0xf88a4338 bmdma 0x00000000 irq 11                                                                                      
Jun 19 00:55:10 AMBERT kernel: [   30.853785] scsi0 : sata_promise                                                                                                                                               
Jun 19 00:55:10 AMBERT kernel: [   31.376686] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)                                                                                                             
Jun 19 00:55:10 AMBERT kernel: [   31.415311] ata1.00: ata_hpa_resize 1: sectors = 240121728, hpa_sectors = 240121728                                                                                            
Jun 19 00:55:10 AMBERT kernel: [   31.415316] ata1.00: ATA-7: Maxtor 6Y120M0, YAR51EW0, max UDMA/133                                                                                                             
Jun 19 00:55:10 AMBERT kernel: [   31.415319] ata1.00: 240121728 sectors, multi 0: LBA                                                                                                                           
Jun 19 00:55:10 AMBERT kernel: [   31.491586] ata1.00: ata_hpa_resize 1: sectors = 240121728, hpa_sectors = 240121728                                                                                            
Jun 19 00:55:10 AMBERT kernel: [   31.491590] ata1.00: configured for UDMA/133                                                                                                                                   
Jun 19 00:55:10 AMBERT kernel: [   31.491604] scsi1 : sata_promise                                                                                                                                               
Jun 19 00:55:10 AMBERT kernel: [   31.962690] ohci1394: fw-host0: SelfID received outside of bus reset sequence                                                                                                  
Jun 19 00:55:10 AMBERT kernel: [   32.115062] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)                                                                                                             
Jun 19 00:55:10 AMBERT kernel: [   32.163686] ata2.00: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 488397168                                                                                            
Jun 19 00:55:10 AMBERT kernel: [   32.163695] ata2.00: ATA-7: SAMSUNG SP2504C, VT100-41, max UDMA7                                                                                                               
Jun 19 00:55:10 AMBERT kernel: [   32.163698] ata2.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 0/32)                                                                                                        
Jun 19 00:55:10 AMBERT kernel: [   32.215394] ata2.00: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 488397168                                                                                            
Jun 19 00:55:10 AMBERT kernel: [   32.215403] ata2.00: configured for UDMA/133                                                                                                                                   
Jun 19 00:55:10 AMBERT kernel: [   32.215417] scsi2 : sata_promise                                                                                                                                               
Jun 19 00:55:10 AMBERT kernel: [   32.276809] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000010dc0031f6b1]                                                                                                    
Jun 19 00:55:10 AMBERT kernel: [   32.374846] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6Y120M0   YAR5 PQ: 0 ANSI: 5                                                                                       
Jun 19 00:55:10 AMBERT kernel: [   32.375202] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG SP2504C  VT10 PQ: 0 ANSI: 5                                                                                       
Jun 19 00:55:10 AMBERT kernel: [   32.459275] SCSI device sda: 240121728 512-byte hdwr sectors (122942 MB)                                                                                                       
Jun 19 00:55:10 AMBERT kernel: [   32.459293] sda: Write Protect is off                                                                                                                                          
Jun 19 00:55:10 AMBERT kernel: [   32.459295] sda: Mode Sense: 00 3a 00 00                                                                                                                                       
Jun 19 00:55:10 AMBERT kernel: [   32.459314] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA                                                                             
Jun 19 00:55:10 AMBERT kernel: [   32.459389] SCSI device sda: 240121728 512-byte hdwr sectors (122942 MB)                                                                                                       
Jun 19 00:55:10 AMBERT kernel: [   32.459400] sda: Write Protect is off                                                                                                                                          
Jun 19 00:55:10 AMBERT kernel: [   32.459402] sda: Mode Sense: 00 3a 00 00                                                                                                                                       
Jun 19 00:55:10 AMBERT kernel: [   32.459419] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA                                                                             
Jun 19 00:55:10 AMBERT kernel: [   32.459424]  sda: sda1                                                                                                                                                         
Jun 19 00:55:10 AMBERT kernel: [   32.477235] sd 0:0:0:0: Attached scsi disk sda

Looks okay, but then...


> Jun 20 01:30:04 AMBERT kernel: [ 2597.160755] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jun 20 01:30:04 AMBERT kernel: [ 2597.160797] ata1.00: cmd c8/00:08:bf:81:3d/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
Jun 20 01:30:04 AMBERT kernel: [ 2597.160799]          res 51/40:00:bf:81:3d/00:00:00:00:00/e0 Emask 0x9 (media error)
Jun 20 01:30:04 AMBERT kernel: [ 2597.183603] ata1.00: ata_hpa_resize 1: sectors = 240121728, hpa_sectors = 240121728
Jun 20 01:30:04 AMBERT kernel: [ 2597.203573] ata1.00: ata_hpa_resize 1: sectors = 240121728, hpa_sectors = 240121728
Jun 20 01:30:04 AMBERT kernel: [ 2597.203577] ata1.00: configured for UDMA/100
Jun 20 01:30:04 AMBERT kernel: [ 2597.203588] ata1: EH complete
Jun 20 01:30:05 AMBERT kernel: [ 2598.442934] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jun 20 01:30:05 AMBERT kernel: [ 2598.442968] ata1.00: cmd c8/00:08:bf:81:3d/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
Jun 20 01:30:05 AMBERT kernel: [ 2598.442970]          res 51/40:00:bf:81:3d/00:00:00:00:00/e0 Emask 0x9 (media error)
Jun 20 01:30:05 AMBERT kernel: [ 2598.462399] ata1.00: ata_hpa_resize 1: sectors = 240121728, hpa_sectors = 240121728
Jun 20 01:30:05 AMBERT kernel: [ 2598.482382] ata1.00: ata_hpa_resize 1: sectors = 240121728, hpa_sectors = 240121728
Jun 20 01:30:05 AMBERT kernel: [ 2598.482386] ata1.00: configured for UDMA/100
Jun 20 01:30:05 AMBERT kernel: [ 2598.482391] ata1: EH complete
Jun 20 01:30:08 AMBERT kernel: [ 2601.015643] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jun 20 01:30:08 AMBERT kernel: [ 2601.015677] ata1.00: cmd c8/00:08:bf:81:3d/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
Jun 20 01:30:08 AMBERT kernel: [ 2601.015679]          res 51/01:00:bf:81:3d/00:00:00:00:00/e0 Emask 0x1 (device error)
Jun 20 01:30:08 AMBERT kernel: [ 2601.030019] ata1.00: ata_hpa_resize 1: sectors = 240121728, hpa_sectors = 240121728
Jun 20 01:30:08 AMBERT kernel: [ 2601.049982] ata1.00: ata_hpa_resize 1: sectors = 240121728, hpa_sectors = 240121728
Jun 20 01:30:08 AMBERT kernel: [ 2601.049986] ata1.00: configured for UDMA/100
Jun 20 01:30:08 AMBERT kernel: [ 2601.049991] ata1: EH complete
Jun 20 01:30:09 AMBERT kernel: [ 2602.156277] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jun 20 01:30:09 AMBERT kernel: [ 2602.156311] ata1.00: cmd c8/00:08:bf:81:3d/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
Jun 20 01:30:09 AMBERT kernel: [ 2602.156313]          res 51/40:00:bf:81:3d/00:00:00:00:00/e0 Emask 0x9 (media error)
Jun 20 01:30:09 AMBERT kernel: [ 2602.178948] ata1.00: ata_hpa_resize 1: sectors = 240121728, hpa_sectors = 240121728
Jun 20 01:30:09 AMBERT kernel: [ 2602.198910] ata1.00: ata_hpa_resize 1: sectors = 240121728, hpa_sectors = 240121728
Jun 20 01:30:09 AMBERT kernel: [ 2602.198914] ata1.00: configured for UDMA/100
Jun 20 01:30:09 AMBERT kernel: [ 2602.198920] ata1: EH complete

ata1 is the Maxtor disk...

Is there anyone who can help me with this, or maybe i need to change some settings etc..

Thanx Gil

---

### Post by jpeddicord on 2007-06-20
Are you using a custom kernel? Because I have only seen these errors so far from Gutsy.
If you are on a custom kernel, you may want to revert back to a supported one. That should help with the problem.

Jacob

---

### Post by MR.GIL on 2007-06-22
Nope, it is a standard install no speciall stuff there.. and no upgrade or anything clean install from 7.04 disc

---

### Post by MattDTownsend on 2007-06-26
Any of this sounding familiar?

[http://ubuntuforums.org/showthread.php?t=484576&highlight=emask](http://ubuntuforums.org/showthread.php?t=484576&highlight=emask)

[https://bugs.launchpad.net/ubuntu/+s....20/+bug/64587](https://bugs.launchpad.net/ubuntu/+s....20/+bug/64587)
[https://bugs.launchpad.net/ubuntu/+s....20/+bug/84603](https://bugs.launchpad.net/ubuntu/+s....20/+bug/84603)

---

### Post by MR.GIL on 2007-06-26
yes the last two does sound similar, but i dont have any optical drive attached.. only HD's

---

### Post by MattDTownsend on 2007-06-26
Hmm.  There's a solution there that involves blacklisting certain modules.

> 

I've solved the problem editing /etc/initramfs-tools/modules, and adding this lines:

piix
ide_generic
ide_cd
ide_disk

# blacklist bad driver
blacklist ata_piix

# prevent unnecessary modules from being loaded (you don't need to do this)
blacklist ata_generic
blacklist libata
blacklist scsi_mod

after editing:

sudo update-initramfs -u

after reboot I have my hard disks with the old fashioned /dev/hd*, without bugs!!!:)


Now, the problem with this is that it shuts DMA off, and you will probably have to make sure your fstab and menu.lst point in the right direction. . .if it changes things from sda to hda.  Things will suck hard without DMA, but it may be worth trying as a trouble shoot.

Also have a live-cd handy in case you need to remove those additional lines in the event of non-booting.

---

### Post by tonymaro on 2007-06-28
I'm seeing the same thing on a Tyan dual processor opteron board.
[http://www.maro.net/ossramblings.php?itemid=326]("http://www.maro.net/ossramblings.php?itemid=326")

So far I've had no luck solving this issue.  Setting apci=off had no effect.  Having a CD in (or not in) the drive has no effect.

I didn't notice any issues until I tried to set up a software RAID 1 between two 500 GB HD's (independent of the boot drive.)

I did notice that my BIOS supports three SATA modes: RAID, SATA and PATA.  I was running SATA.  I've switched to PATA and trying again.  I'll try to report back my finding.

Has anyone else had any luck yet?

---

### Post by tonymaro on 2007-07-02
Well I finally solved my issue.  Turns out one of my Barracuda's were bad.  As long as it was connected to the machine, every drive on the system would fail a test.  Once it was disconnected my SATA controller stopped locking up.

---

### Post by daddydoc on 2007-07-07
did you actually get ubuntu 7.04 to work in raid 1?   Did you use the alternate cd version or the desktop?

If you did use the desktop, could you please point me to the instructions on how to setup raid 1 with 7.04?

I successfully used 6.10 alternate cd to setup raid1, but having trouble with a fresh install with 7.10 aternate cd for raid1.

thanks in advance
Daddydoc

---

