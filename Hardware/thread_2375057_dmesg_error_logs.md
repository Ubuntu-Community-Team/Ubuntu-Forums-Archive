---
title: "dmesg error logs"
date: 2017-10-21
forum: Hardware
---

### Post by anandpushkar on 2017-10-21
My ubuntu system is freezes now and then.
 Following is the data from demsg:
[ 1701.973924] ata1.00: exception Emask 0x0 SAct 0x80000 SErr 0x0 action 0x0
[ 1701.973935] ata1.00: irq_stat 0x40000008
[ 1701.973942] ata1.00: failed command: READ FPDMA QUEUED
[ 1701.973954] ata1.00: cmd 60/01:98:41:ff:1d/00:00:13:00:00/40 tag 19 ncq dma 512 in
                        res 51/40:01:41:ff:1d/00:00:13:00:00/40 Emask 0x409 (media error) <F>
[ 1701.973960] ata1.00: status: { DRDY ERR }
[ 1701.973965] ata1.00: error: { UNC }
[ 1701.976056] ata1.00: configured for UDMA/100
[ 1701.976082] sd 0:0:0:0: [sda] tag#19 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1701.976088] sd 0:0:0:0: [sda] tag#19 Sense Key : Medium Error [current] 
[ 1701.976093] sd 0:0:0:0: [sda] tag#19 Add. Sense: Unrecovered read error - auto reallocate failed
[ 1701.976099] sd 0:0:0:0: [sda] tag#19 CDB: Read(10) 28 00 13 1d ff 41 00 00 01 00
[ 1701.976103] print_req_error: I/O error, dev sda, sector 320732993
[ 1701.976157] ata1: EH complete
[ 1705.095217] ata1.00: exception Emask 0x0 SAct 0x800000 SErr 0x0 action 0x0
[ 1705.095229] ata1.00: irq_stat 0x40000008
[ 1705.095236] ata1.00: failed command: READ FPDMA QUEUED
[ 1705.095248] ata1.00: cmd 60/01:b8:41:ff:1d/00:00:13:00:00/40 tag 23 ncq dma 512 in
                        res 51/40:01:41:ff:1d/00:00:13:00:00/40 Emask 0x409 (media error) <F>
[ 1705.095254] ata1.00: status: { DRDY ERR }
[ 1705.095257] ata1.00: error: { UNC }
[ 1705.097399] ata1.00: configured for UDMA/100
[ 1705.097426] sd 0:0:0:0: [sda] tag#23 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1705.097432] sd 0:0:0:0: [sda] tag#23 Sense Key : Medium Error [current] 
[ 1705.097437] sd 0:0:0:0: [sda] tag#23 Add. Sense: Unrecovered read error - auto reallocate failed
[ 1705.097443] sd 0:0:0:0: [sda] tag#23 CDB: Read(10) 28 00 13 1d ff 41 00 00 01 00
[ 1705.097447] print_req_error: I/O error, dev sda, sector 320732993
[ 1705.097488] FAT-fs (sda10): FAT read failed (blocknr 30529)
[ 1705.097497] ata1: EH complete

Data from smartctl -a /dev/sda is [here]("https://pastebin.com/cEy92xt2")

I am running ubuntu 17.10 on Intel® Core™ i5-2520M CPU @ 2.50GHz × 4 with 4gb ram

---

### Post by jeremy31 on 2017-10-21
Back up your data now.  I have seen ata1.00: failed command: READ FPDMA QUEUED myself and it wasn't very long and the hard drive quit working

---

### Post by efflandt on 2017-10-21
Drives normally reserve space to automatically remap in place of bad sectors independent from the OS. Although, you may have some other possibly electrical/electronic issue or it cannot read the bad spot to remap it (Current_Pending_Sector 1).

In the rare cases that I have seen DRDY ERR it makes me thing "dirty" and to promptly backup anything not backed up from the drive that I want to save. Raw_Read_Error_Rate 100466957 and ATA Error Count: 7690 do not look good.

The drive I have with Power_On_Hours 37239 has zeros for Raw_Read_Error_Rate, Reallocated_Sector_Ct, Reallocated_Event_Count, Current_Pending_Sector, etc. and:

SMART Error Log Version: 1
No Errors Logged

If you can boot an alternate Linux system (or live/install iso) you might try repairing the drive and then locking out badblocks with following commands followed by a space and the partition (like /dev/sda1, etc.). The -f option in each case is to force the check even if it thinks it was previously successful. 1st command attempts to automatically fix what is wrong and tell you what it cannot fix, 2nd does non-destructive read-write test and adds any bad blocks to badblocks list so the system will avoid using those:```
sudo e2fsck -fp
sudo e2fsck -fcck
```

One of the scariest things you can see when you boot is "Immanent drive failure" from BIOS. The only time I ever saw that, the next time I booted, it wouldn't. But it was a Win98 drive that was rarely used, had been making strange noises, and I had Linux on a separate drive. So I simply removed that drive and set up Linux as the primary boot drive. Fortunately other drive failures have been gradual giving me time to prepare.

---

