---
title: "SSD failure"
date: 2016-03-19
forum: Hardware
---

### Post by ghb321-gmail on 2016-03-19
Could someone tell me what's going on on my SSD?

Log file:
Mar 19 21:56:19 localhost kernel: [  266.833101] sd 0:0:0:0: [sda]  
Mar 19 21:56:19 localhost kernel: [  266.833104] Sense Key : Aborted Command [current] [descriptor]
Mar 19 21:56:19 localhost kernel: [  266.833109] Descriptor sense data with sense descriptors (in hex):
Mar 19 21:56:19 localhost kernel: [  266.833112]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Mar 19 21:56:19 localhost kernel: [  266.833125]         00 00 00 00 
Mar 19 21:56:19 localhost kernel: [  266.833131] sd 0:0:0:0: [sda]  
Mar 19 21:56:19 localhost kernel: [  266.833134] Add. Sense: No additional sense information
Mar 19 21:56:19 localhost kernel: [  266.833137] sd 0:0:0:0: [sda] CDB: 
Mar 19 21:56:19 localhost kernel: [  266.833140] Write same(16): 93 08 00 00 00 00 05 dc 10 70 00 00 00 08 00 00
Mar 19 21:56:19 localhost kernel: [  266.833156] end_request: I/O error, dev sda, sector 98308208
Mar 19 21:56:19 localhost kernel: [  266.834841] EXT4-fs (sda5): discard request in group:98 block:16398 count:1 failed with -5
Mar 19 21:56:55 localhost kernel: [  302.843551] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Mar 19 21:56:55 localhost kernel: [  302.845070] ata1.00: BMDMA stat 0x65
Mar 19 21:56:55 localhost kernel: [  302.846550] ata1.00: failed command: DATA SET MANAGEMENT
Mar 19 21:56:55 localhost kernel: [  302.848036] ata1.00: cmd 06/01:01:00:00:00/00:00:00:00:00/a0 tag 26 dma 512 out
Mar 19 21:56:55 localhost kernel: [  302.848036]          res 51/04:01:00:00:00/04:00:00:00:00/a0 Emask 0x1 (device error)
Mar 19 21:56:55 localhost kernel: [  302.851004] ata1.00: status: { DRDY ERR }
Mar 19 21:56:55 localhost kernel: [  302.852518] ata1.00: error: { ABRT }
Mar 19 21:56:55 localhost kernel: [  302.854020] ata1.00: device reported invalid CHS sector 0
Mar 19 21:56:55 localhost kernel: [  302.854031] sd 0:0:0:0: [sda]  
Mar 19 21:56:55 localhost kernel: [  302.854034] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Mar 19 21:56:55 localhost kernel: [  302.854037] sd 0:0:0:0: [sda]  
Mar 19 21:56:55 localhost kernel: [  302.854040] Sense Key : Aborted Command [current] [descriptor]
Mar 19 21:56:55 localhost kernel: [  302.854045] Descriptor sense data with sense descriptors (in hex):
Mar 19 21:56:55 localhost kernel: [  302.854048]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
Mar 19 21:56:55 localhost kernel: [  302.854061]         00 00 00 00 
Mar 19 21:56:55 localhost kernel: [  302.854067] sd 0:0:0:0: [sda]  
Mar 19 21:56:55 localhost kernel: [  302.854070] Add. Sense: No additional sense information
Mar 19 21:56:55 localhost kernel: [  302.854074] sd 0:0:0:0: [sda] CDB: 
Mar 19 21:56:55 localhost kernel: [  302.854076] Write same(16): 93 08 00 00 00 00 05 db 40 78 00 00 00 08 00 00
Mar 19 21:56:55 localhost kernel: [  302.854091] end_request: I/O error, dev sda, sector 98254968
Mar 19 21:56:55 localhost kernel: [  302.856250] EXT4-fs (sda5): discard request in group:98 block:9743 count:1 failed with -5

sudo smartctl --all /dev/sda




ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x0000   ---   ---   ---    Old_age   Offline      -       7
  9 Power_On_Hours          0x0000   ---   ---   ---    Old_age   Offline      -       25927
 12 Power_Cycle_Count       0x0000   ---   ---   ---    Old_age   Offline      -       3477
184 Initial_Bad_Block_Count 0x0000   ---   ---   ---    Old_age   Offline      -       4
195 Program_Failure_Blk_Ct  0x0000   ---   ---   ---    Old_age   Offline      -       2
196 Erase_Failure_Blk_Ct    0x0000   ---   ---   ---    Old_age   Offline      -       5
197 Read_Failure_Blk_Ct     0x0000   ---   ---   ---    Old_age   Offline      -       0
198 Read_Sectors_Tot_Ct     0x0000   ---   ---   ---    Old_age   Offline      -       25312189249
199 Write_Sectors_Tot_Ct    0x0000   ---   ---   ---    Old_age   Offline      -       14371197733
200 Read_Commands_Tot_Ct    0x0000   ---   ---   ---    Old_age   Offline      -       644635838
201 Write_Commands_Tot_Ct   0x0000   ---   ---   ---    Old_age   Offline      -       287858364
202 Error_Bits_Flash_Tot_Ct 0x0000   ---   ---   ---    Old_age   Offline      -       4726119
203 Corr_Read_Errors_Tot_Ct 0x0000   ---   ---   ---    Old_age   Offline      -       4507241
204 Bad_Block_Full_Flag     0x0000   ---   ---   ---    Old_age   Offline      -       0
205 Max_PE_Count_Spec       0x0000   ---   ---   ---    Old_age   Offline      -       100000
206 Min_Erase_Count         0x0000   ---   ---   ---    Old_age   Offline      -       59
207 Max_Erase_Count         0x0000   ---   ---   ---    Old_age   Offline      -       17025
208 Average_Erase_Count     0x0000   ---   ---   ---    Old_age   Offline      -       4246
209 Remaining_Lifetime_Perc 0x0000   ---   ---   ---    Old_age   Offline      -       96
210 Indilinx_Internal       0x0000   ---   ---   ---    Old_age   Offline      -       237
211 SATA_Error_Ct_CRC       0x0000   ---   ---   ---    Old_age   Offline      -       0

Is disk broken?

---

