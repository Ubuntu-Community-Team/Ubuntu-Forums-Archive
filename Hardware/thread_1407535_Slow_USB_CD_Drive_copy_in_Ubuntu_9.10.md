---
title: "Slow USB CD Drive copy in Ubuntu 9.10"
date: 2010-02-15
forum: Hardware
---

### Post by clenched_sphere on 2010-02-15
Hi all.

I've had this issue for a while in Karmic, I have an old IDE laptop cd drive that I have in an IDE -USB 2.0 enclosure, so I can do without a big clunky 5" drive taking up space in my desktop case.

Have been using it will (in total) 2 laptops and my desktop (while running xp or win7) with no issues, regularly use it to install games DVD's, copy music cd's etc.

However, when I try to use it in Karmic to import CD's in Rythmbox or Exaile, it's pathetically slow and plods along at next to nothing. AFAIK, this isn't a hardware issue with my mainboard or the drive itself, they have been tried and tested using other machines and with other OS, using different USB ports also.

I thought it might be trying to import using FLAC in epic ultra high quality, but after changing this to mp3 no real difference. 

checking dmesg after plugging it in and loading rythmbox gave some interesting output:

[ 3109.936025] usb 1-1: new high speed USB device using ehci_hcd and address 10                                                                                                                          
[ 3110.070018] usb 1-1: configuration #1 chosen from 1 choice                                                                                                                                            
[ 3110.070510] scsi10 : SCSI emulation for USB Mass Storage devices                                                                                                                                      
[ 3110.070625] usb-storage: device found at 10                                                                                                                                                           
[ 3110.070626] usb-storage: waiting for device to settle before scanning                                                                                                                                 
[ 3115.068828] usb-storage: device scan complete                                                                                                                                                         
[ 3115.069798] scsi 10:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-K14  1.10 PQ: 0 ANSI: 0                                                                                                             
[ 3115.112167] sr1: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray                                                                                                                             
[ 3115.112281] sr 10:0:0:0: Attached scsi CD-ROM sr1                                                                                                                                                     
[ 3115.112341] sr 10:0:0:0: Attached scsi generic sg2 type 5                                                                                                                                             
[ 3128.197827] sr 10:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE                                                                                                                        
[ 3128.197833] sr 10:0:0:0: [sr1] Sense Key : Illegal Request [current]                                                                                                                                  
[ 3128.197836] Info fld=0x0                                                                                                                                                                              
[ 3128.197838] sr 10:0:0:0: [sr1] Add. Sense: Illegal mode for this track                                                                                                                                
[ 3128.197843] end_request: I/O error, dev sr1, sector 0                                                                                                                                                 
[ 3128.197847] __ratelimit: 60 callbacks suppressed                                                                                                                                                      
[ 3128.197849] Buffer I/O error on device sr1, logical block 0                                                                                                                                           
[ 3128.197851] Buffer I/O error on device sr1, logical block 1                                                                                                                                           
[ 3128.197853] Buffer I/O error on device sr1, logical block 2                                                                                                                                           
[ 3128.197855] Buffer I/O error on device sr1, logical block 3                                                                                                                                           
[ 3128.197857] Buffer I/O error on device sr1, logical block 4                                                                                                                                           
[ 3128.197858] Buffer I/O error on device sr1, logical block 5                                                                                                                                           
[ 3128.197860] Buffer I/O error on device sr1, logical block 6                                                                                                                                           
[ 3128.197862] Buffer I/O error on device sr1, logical block 7                                                                                                                                           
[ 3128.197865] Buffer I/O error on device sr1, logical block 8                                                                                                                                           
[ 3128.197867] Buffer I/O error on device sr1, logical block 9                                                                                                                                           
[ 3128.205576] sr 10:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE                                                                                                                        
[ 3128.205578] sr 10:0:0:0: [sr1] Sense Key : Illegal Request [current]                                                                                                                                  
[ 3128.205581] Info fld=0x10                                                                                                                                                                             
[ 3128.205582] sr 10:0:0:0: [sr1] Add. Sense: Illegal mode for this track                                                                                                                                
[ 3128.205585] end_request: I/O error, dev sr1, sector 64                                                                                                                                                
[ 3128.212826] sr 10:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE                                                                                                                        
[ 3128.212828] sr 10:0:0:0: [sr1] Sense Key : Illegal Request [current]                                                                                                                                  
[ 3128.212830] Info fld=0x20                                                                                                                                                                             
[ 3128.212831] sr 10:0:0:0: [sr1] Add. Sense: Illegal mode for this track
[ 3128.212835] end_request: I/O error, dev sr1, sector 128
[ 3128.219831] sr 10:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3128.219834] sr 10:0:0:0: [sr1] Sense Key : Illegal Request [current]
[ 3128.219836] Info fld=0x30
[ 3128.219837] sr 10:0:0:0: [sr1] Add. Sense: Illegal mode for this track
[ 3128.219840] end_request: I/O error, dev sr1, sector 192
[ 3128.232458] sr 10:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3128.232460] sr 10:0:0:0: [sr1] Sense Key : Illegal Request [current]
[ 3128.232462] Info fld=0x0
[ 3128.232464] sr 10:0:0:0: [sr1] Add. Sense: Illegal mode for this track
[ 3128.232467] end_request: I/O error, dev sr1, sector 0
[ 3128.315349] sr 10:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3128.315354] sr 10:0:0:0: [sr1] Sense Key : Illegal Request [current]
[ 3128.315357] Info fld=0x0
[ 3128.315359] sr 10:0:0:0: [sr1] Add. Sense: Illegal mode for this track
[ 3128.315363] end_request: I/O error, dev sr1, sector 0
[ 3128.322469] sr 10:0:0:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3128.322472] sr 10:0:0:0: [sr1] Sense Key : Illegal Request [current]
[ 3128.322474] Info fld=0x0
[ 3128.322475] sr 10:0:0:0: [sr1] Add. Sense: Illegal mode for this track
[ 3128.322478] end_request: I/O error, dev sr1, sector 0


If anyone has any ideas about where to go from here, I would be grateful for them.

Thanks

---

