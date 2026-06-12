---
title: "some harddrive issues"
date: 2010-03-20
forum: Hardware
---

### Post by kouter on 2010-03-20
karmic server keeps changing permissions on one of my harddrives to read only. owner and group owner are under my login, but won't allow myself or sudo to chmod +w.

dmesg | grep ata1
```
[    0.500849] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xf400 irq 23
[    0.990014] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)         
[    1.010219] ata1.00: ATA-6: WDC WD3000JD-00KLB0, 08.05J08, max UDMA/100    
[    1.010223] ata1.00: 586072368 sectors, multi 16: LBA48                    
[    1.050244] ata1.00: configured for UDMA/100                               
[   24.811924] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x400000 action 0x6 
[   24.811928] ata1.00: BMDMA stat 0x24                                       
[   24.811932] ata1: SError: { Handshk }                                      
[   24.811941] ata1.00: cmd ca/00:08:79:98:2d/00:00:00:00:00/e0 tag 0 dma 4096 out
[   24.811946] ata1.00: status: { DRDY ERR }                                      
[   24.811948] ata1.00: error: { ICRC ABRT }                                      
[   24.811956] ata1: hard resetting link                                          
[   24.811958] ata1: nv: skipping hardreset on occupied port                      
[   25.300025] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)             
[   25.370596] ata1.00: configured for UDMA/100                                   
[   25.370616] ata1: EH complete                                                  
[   25.370908] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x400000 action 0x6     
[   25.370913] ata1.00: BMDMA stat 0x24                                           
[   25.370916] ata1: SError: { Handshk }                                          
[   25.370925] ata1.00: cmd ca/00:08:79:98:2d/00:00:00:00:00/e0 tag 0 dma 4096 out
[   25.370930] ata1.00: status: { DRDY ERR }                                      
[   25.370932] ata1.00: error: { ICRC ABRT }                                      
[   25.370939] ata1: hard resetting link                                          
[   25.370942] ata1: nv: skipping hardreset on occupied port                      
[   25.862305] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)             
[   25.922079] ata1.00: configured for UDMA/100                                   
[   25.922096] ata1: EH complete                                                  
[   25.922282] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x400000 action 0x6     
[   25.922287] ata1.00: BMDMA stat 0x24                                           
[   25.922291] ata1: SError: { Handshk }                                          
[   25.922300] ata1.00: cmd ca/00:08:79:98:2d/00:00:00:00:00/e0 tag 0 dma 4096 out
[   25.922305] ata1.00: status: { DRDY ERR }
[   25.922308] ata1.00: error: { ICRC ABRT }
[   25.922315] ata1: hard resetting link
[   25.922318] ata1: nv: skipping hardreset on occupied port
[   26.411864] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   26.473960] ata1.00: configured for UDMA/100
[   26.473976] ata1: EH complete
[   26.556571] ata1: limiting SATA link speed to 1.5 Gbps
[   26.556577] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x1c00000 action 0x6
[   26.556581] ata1.00: BMDMA stat 0x24
[   26.556585] ata1: SError: { Handshk LinkSeq TrStaTrns }
[   26.556595] ata1.00: cmd ca/00:08:79:98:2d/00:00:00:00:00/e0 tag 0 dma 4096 out
[   26.556600] ata1.00: status: { DRDY ERR }
[   26.556602] ata1.00: error: { ICRC ABRT }
[   26.556610] ata1: hard resetting link
[   26.556612] ata1: nv: skipping hardreset on occupied port
[   27.050041] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   27.120308] ata1.00: configured for UDMA/100
[   27.120330] ata1: EH complete
```seems like the issue is on boot-up?

---

### Post by tgalati4 on 2010-03-20
Looks like a SATA communication issue.  Could be a bad cable; try a different one.  Could be a bad port; try a different one.  Could be a bad SATA controller on the motherboard.  Could be a bad SATA controller on the disk drive.

Could be a loose power connector on the hard drive.  Could be a wonky power supply.

---

### Post by kouter on 2010-03-21
sudo e2fsck -c -f -v /dev/sda5

fixed the issue, couple hundred thousand bad sectors, some bad inodes and directories. kinda still curious why something like this would happen.

more info at [http://ubuntuforums.org/showthread.php?t=937872](http://ubuntuforums.org/showthread.php?t=937872) on the fix

---

### Post by tgalati4 on 2010-03-21
How many hours on the the drive?  If you haven't, install smartmontools:

sudo apt-get install smartmontools

sudo smartctl -a /dev/sda

---

