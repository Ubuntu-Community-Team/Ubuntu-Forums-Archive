---
title: "Hard drive errors or bug ?"
date: 2009-01-12
forum: Hardware
---

### Post by oygle on 2009-01-12
Using Intrepid with all updates, and noticed in the syslog

> Jan 13 12:09:14  kernel: [13879.280481] ata1.00: exception Emask 0x2 SAct 0x0 SErr 0x400 action 0x6
Jan 13 12:09:14  kernel: [13879.280491] ata1.00: irq_stat 0x44000001
Jan 13 12:09:14  kernel: [13879.280498] ata1: SError: { Proto }
Jan 13 12:09:14  kernel: [13879.280509] ata1.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Jan 13 12:09:14  kernel: [13879.280512]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Jan 13 12:09:14  kernel: [13879.280515]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x2 (HSM violation)
Jan 13 12:09:14  kernel: [13879.280522] ata1.00: status: { DRDY ERR }
Jan 13 12:09:14  kernel: [13879.280534] ata1: hard resetting link
Jan 13 12:09:15  kernel: [13880.716032] ata1: SATA link down (SStatus 0 SControl 300)
Jan 13 12:09:16  kernel: [13881.298451] ata1: hard resetting link
Jan 13 12:09:17  kernel: [13882.456040] ata1: SATA link down (SStatus 0 SControl 300)
Jan 13 12:09:17  kernel: [13883.045441] ata1: hard resetting link
Jan 13 12:09:18  kernel: [13883.712049] ata1: SATA link down (SStatus 0 SControl 300)
Jan 13 12:09:18  kernel: [13883.712063] ata1.00: disabled
Jan 13 12:09:18  kernel: [13883.712087] ata1: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x9 t4
Jan 13 12:09:18  kernel: [13883.712095] ata1: irq_stat 0x00400040, connection status changed
Jan 13 12:09:18  kernel: [13883.712106] ata1: hard resetting link
Jan 13 12:09:19  kernel: [13884.948068] ata1: SATA link down (SStatus 0 SControl 300)
Jan 13 12:09:19  kernel: [13884.948111] ata1: EH complete
Jan 13 12:09:19  kernel: [13884.948119] ata1.00: detaching (SCSI 0:0:0:0)
Jan 13 12:09:20  kernel: [13885.580551] ata1: exception Emask 0x10 SAct 0x0 SErr 0x4050000 action 0xe frozen
Jan 13 12:09:20  kernel: [13885.580562] ata1: irq_stat 0x00400040, connection status changed
Jan 13 12:09:20  kernel: [13885.580569] ata1: SError: { PHYRdyChg CommWake DevExch }
Jan 13 12:09:20  kernel: [13885.580583] ata1: hard resetting link
Jan 13 12:09:21  kernel: [13886.560044] ata1: SATA link down (SStatus 0 SControl 300)
Jan 13 12:09:21  kernel: [13886.560061] ata1: EH complete
Jan 13 12:09:22  kernel: [13887.558437] ata1: exception Emask 0x10 SAct 0x0 SErr 0x4000000 action 0xe frozen
Jan 13 12:09:22  kernel: [13887.558448] ata1: irq_stat 0x00000040, connection status changed
Jan 13 12:09:22  kernel: [13887.558455] ata1: SError: { DevExch }
Jan 13 12:09:22  kernel: [13887.558469] ata1: hard resetting link
Jan 13 12:09:23  kernel: [13888.280045] ata1: SATA link down (SStatus 0 SControl 300)
Jan 13 12:09:23  kernel: [13888.280062] ata1: EH complete
Jan 13 12:09:26  kernel: [13892.224668] ata1: exception Emask 0x10 SAct 0x0 SErr 0x4000000 action 0xe frozen
Jan 13 12:09:26  kernel: [13892.224677] ata1: irq_stat 0x00000040, connection status changed
Jan 13 12:09:26  kernel: [13892.224684] ata1: SError: { DevExch }
Jan 13 12:09:26  kernel: [13892.224724] ata1: hard resetting link
Jan 13 12:09:28  kernel: [13893.620035] ata1: SATA link down (SStatus 0 SControl 300)
Jan 13 12:09:28  kernel: [13893.620052] ata1: EH complete
Jan 13 12:09:30  kernel: [13895.282708] ata1: exception Emask 0x10 SAct 0x0 SErr 0x4000000 action 0xe frozen
Jan 13 12:09:30  kernel: [13895.282722] ata1: irq_stat 0x00000040, connection status changed
Jan 13 12:09:30  kernel: [13895.282729] ata1: SError: { DevExch }

Noticed this bug - [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/163637](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/163637)

but as the kernel I'm running is for Intrepid, it should be fixed.

is this a bug or hard drive errors ?

Oygle

---

### Post by oygle on 2009-01-13
Still getting these

> Jan 14 10:44:24  kernel: [  453.996692] ata1: hard resetting link
Jan 14 10:44:27  kernel: [  456.228041] ata1: SATA link down (SStatus 1 SControl 300)
Jan 14 10:44:27  kernel: [  456.228058] ata1: EH complete
Jan 14 10:44:31  kernel: [  460.405071] ata1: hard resetting link
Jan 14 10:44:32  kernel: [  461.128033] ata1: SATA link down (SStatus 0 SControl 300)
Jan 14 10:44:32  kernel: [  461.128048] ata1: EH complete

---

### Post by oygle on 2009-01-14
Some more information in syslog

> Jan 14 19:37:21  kernel: [    3.509093] pata_acpi 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jan 14 19:37:21  kernel: [    3.509180] pata_acpi 0000:00:1f.1: PCI INT A disabled
Jan 14 19:37:21  kernel: [    3.509213] pata_acpi 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jan 14 19:37:21  kernel: [    3.509271] pata_acpi 0000:00:1f.2: PCI INT B disabled
Jan 14 19:37:21  kernel: [    3.530575] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jan 14 19:37:21  kernel: [    3.530832] ahci 0000:00:1f.2: AHCI 0001.0000 32 slots 4 ports 1.5 Gbps 0xf impl IDE mode
Jan 14 19:37:21  kernel: [    3.530840] ahci 0000:00:1f.2: flags: 64bit ncq pm led slum part 
Jan 14 19:37:21  kernel: [    3.531214] scsi0 : ahci
Jan 14 19:37:21  kernel: [    3.531506] scsi1 : ahci
Jan 14 19:37:21  kernel: [    3.531856] scsi2 : ahci
Jan 14 19:37:21  kernel: [    3.540084] scsi3 : ahci
Jan 14 19:37:21  kernel: [    3.540228] ata1: SATA max UDMA/133 abar m1024@0xcdeffc00 port 0xcdeffd00 irq 19
Jan 14 19:37:21  kernel: [    3.540237] ata2: SATA max UDMA/133 irq_stat 0x00400040, connection status changed irq 19
Jan 14 19:37:21  kernel: [    3.540244] ata3: SATA max UDMA/133 abar m1024@0xcdeffc00 port 0xcdeffe00 irq 19
Jan 14 19:37:21  kernel: [    3.540251] ata4: SATA max UDMA/133 abar m1024@0xcdeffc00 port 0xcdeffe80 irq 19
Jan 14 19:37:21  kernel: [    3.861034] ata1: SATA link down (SStatus 0 SControl 300)
Jan 14 19:37:21  kernel: [    4.359194] ata1: hard resetting link
Jan 14 19:37:21  kernel: [    4.600038] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jan 14 19:37:21  kernel: [    4.603595] ata2.00: ATA-6: ST3200822AS, 3.01, max UDMA/133
Jan 14 19:37:21  kernel: [    4.603599] ata2.00: 390721968 sectors, multi 16: LBA48 
Jan 14 19:37:21  kernel: [    4.607431] ata2.00: configured for UDMA/133
Jan 14 19:37:21  kernel: [    4.940041] ata3: SATA link down (SStatus 0 SControl 300)
Jan 14 19:37:21  kernel: [    5.276031] ata4: SATA link down (SStatus 0 SControl 300)
Jan 14 19:37:21  kernel: [    5.292180] scsi 1:0:0:0: Direct-Access     ATA      ST3200822AS      3.01 PQ: 0 ANSI: 5
Jan 14 19:37:21  kernel: [    5.292350] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jan 14 19:37:21  kernel: [    5.292501] scsi4 : ata_piix
Jan 14 19:37:21  kernel: [    5.292612] scsi5 : ata_piix
Jan 14 19:37:21  kernel: [    5.294796] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
Jan 14 19:37:21  kernel: [    5.294800] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
Jan 14 19:37:21  kernel: [    5.456385] ata5.00: ATAPI: CRD-8483B, 1.02, max UDMA/33
Jan 14 19:37:21  kernel: [    5.464331] ata5.00: configured for UDMA/33

Some possible assoctiated links and bug references to the Linux kernel

[http://ubuntuforums.org/archive/index.php/t-985812.html](http://ubuntuforums.org/archive/index.php/t-985812.html)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269652](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/269652)

[http://bugs.archlinux.org/task/11535](http://bugs.archlinux.org/task/11535)

The kernel info I have is 2.6.27-9-generic (#1 SMP Thu Nov 20 21:57:00 UTC 2008) , and am running Intrepid with all updates.

The hard drive is a Seagate ST3200822AS ,specs:

> 
INTERNAL TRANSFER RATE (Mbytes/sec) ______up to 85.4
       SUSTAINED TRANSFER RATE (MB/sec)__________up to 58
       EXTERNAL TRANSFER RATE (Mbytes/sec) ______up to 150
       PIO/DMA/UDMA MODE (max) __________________4/2/6


and the drives returns these speeds under Ubuntu

```
$ sudo hdparm -tT /dev/sda1


/dev/sda1:
 Timing cached reads:   1800 MB in  2.00 seconds = 899.40 MB/sec
 Timing buffered disk reads:  184 MB in  3.00 seconds =  61.28 MB/sec
$ 
```

Any clues please ?

Oygle

---

### Post by oygle on 2009-01-16
How do I find out what is 'ata1' ?

There are 2 devices on the SATA controller, but how do I find out which one is 'ata1' ?

*Later*: Have been looking through this bug - [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/217920](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/217920)

See these posts down the bottom:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/217920/comments/49](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/217920/comments/49)  -  pointing to SATA cable issue
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/217920/comments/51](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/217920/comments/51)  -  pointing to a BIOS solution

The cable issue is further discussed at [http://ubuntuforums.org/showthread.php?t=598837](http://ubuntuforums.org/showthread.php?t=598837) , wherein a number of posters found that replacing the SATA cables with a better quality one, fixed the problem. Also, one person I think pushed the cable in, to make a better connection.

So, it seems it is at least worth the few $$ for me to go and buy some better quality SATA cables.

Oygle

---

### Post by oygle on 2009-01-27
These errors are still appearing intermitantly. Bug or HDD failure ?

---

### Post by BrooksOfSheffield on 2009-01-27
Do you have blank media in your optical drive when the errors occur?

---

### Post by oygle on 2009-01-27
> **BrooksOfSheffield said:**
> Do you have blank media in your optical drive when the errors occur?

No, I don't, there is no media in the DVD-RW. However, I was wondering if it is the DVD-RW and not the HDD, because if I press the button on the drive to open, it opens then shuts again quickly.

I would have thought/assumed it was definitely the hard drive, but it may be the DVD-RW, it is SATA as well.

Getting these every 30 seconds or so ..

> Jan 28 13:07:15  kernel: [ 7427.056533] ata1.00: exception Emask 0x2 SAct 0x0 SErr 0x400 action 0x6
Jan 28 13:07:15  kernel: [ 7427.056543] ata1.00: irq_stat 0x44000001
Jan 28 13:07:15  kernel: [ 7427.056550] ata1: SError: { Proto }
Jan 28 13:07:15  kernel: [ 7427.056562] ata1.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Jan 28 13:07:15  kernel: [ 7427.056564]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Jan 28 13:07:15  kernel: [ 7427.056567]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x2 (HSM violation)
Jan 28 13:07:15  kernel: [ 7427.056574] ata1.00: status: { DRDY ERR }
Jan 28 13:07:15  kernel: [ 7427.056637] ata1: hard resetting link
Jan 28 13:07:15  kernel: [ 7427.376039] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jan 28 13:07:15  kernel: [ 7427.376824] ata1.00: configured for UDMA/66
Jan 28 13:07:15  kernel: [ 7427.376842] ata1: EH complete

Hmm, now the DVD-RW drive opens and stays open.

---

### Post by oygle on 2009-01-27
Just tried this command

```
# sudo smartctl -a -d ata /dev/sda
```

> 
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.7 and 7200.7 Plus family
Device Model:     ST3200822AS
Serial Number:    *********
Firmware Version: 3.01
User Capacity:    200,049,647,616 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   6
ATA Standard is:  ATA/ATAPI-6 T13 1410D revision 2
Local Time is:    Wed Jan 28 13:22:52 2009 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 ( 430) seconds.
Offline data collection
capabilities: 			 (0x5b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					No General Purpose Logging support.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 ( 111) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   053   048   006    Pre-fail  Always       -       983047
  3 Spin_Up_Time            0x0003   096   096   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       148
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       3
  7 Seek_Error_Rate         0x000f   074   060   030    Pre-fail  Always       -       27844394
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       574
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       151
194 Temperature_Celsius     0x0022   032   059   000    Old_age   Always       -       32
195 Hardware_ECC_Recovered  0x001a   053   048   000    Old_age   Always       -       983047
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%       496         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.



---

### Post by brin on 2009-02-04
Hi, have u got an nvidia card and are using the proprietary nvidia drivers?

---

### Post by oygle on 2009-03-20
> **brin said:**
> Hi, have u got an nvidia card and are using the proprietary nvidia drivers?

Yes, but I don't understand how that could produce hard drive errors in the logs ?

I'm still getting loads of these messages ..

> 
Mar 20 22:18:28  kernel: [24769.036472] ata1.00: exception Emask 0x2 SAct 0x0 SErr 0x80400 action 0x6
Mar 20 22:18:28  kernel: [24769.036485] ata1.00: irq_stat 0x44000001
Mar 20 22:18:28  kernel: [24769.036516] ata1: SError: { Proto 10B8B }
Mar 20 22:18:28  kernel: [24769.036527] ata1.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Mar 20 22:18:28  kernel: [24769.036530]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Mar 20 22:18:28  kernel: [24769.036532]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x2 (HSM violation)
Mar 20 22:18:28  kernel: [24769.036540] ata1.00: status: { DRDY ERR }
Mar 20 22:18:28  kernel: [24769.036550] ata1: hard resetting link
Mar 20 22:18:28  kernel: [24769.357048] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Mar 20 22:18:28  kernel: [24769.358185] ata1.00: configured for UDMA/66
Mar 20 22:18:28  kernel: [24769.358205] ata1: EH complete


Any way to track down what the cause of this is please ?

Running Ubuntu 8.10 (intrepid) , GNOME 2.24.1 (Ubuntu 2008-10-24) , Kernel 2.6.27-11-generic (#1 SMP Thu Jan 29 19:24:39 UTC 2009)

Oygle

---

### Post by oygle on 2009-03-23
Anyone know what the cause of this is please ?

Oygle

---

### Post by brin on 2009-03-23
Hi Oygle,

If you are using Nvidia's drivers you could have the same issue as 

[http://ubuntuforums.org/archive/index.php/t-1037819.html](http://ubuntuforums.org/archive/index.php/t-1037819.html)

Which I believe there is a conflict (possibly irq) between the nvidia drivers and the ahci. Unfortunately I do not know the solution but hopefully this would point you in the right direction.

Regards,
Brinley

---

### Post by oygle on 2009-03-24
Thanks for pointing me to [the thread on Intrepid: SATA SError: { Handshk } / hard resetting link Errors with GDM running]("http://ubuntuforums.org/showthread.php?t=1037819")

Very interesting, and I see they have NVidia drivers, in fact I have 173 and 177 installed, so possibly this is the cause ??

Actually, I already have the VESA drivers installed also - synaptic tell me "X.Org X server -- VESA display driver" , version 1.2.0.0

Maybe I just uninstall NVidia completely, worth a try at least.

Thanks,

Oygle

---

### Post by oygle on 2009-03-29
Uninstalled the NVIDIA drivers, rebooted and no error messages. next day was okay as well, but then the days after that, the same error messages appeared agin.  :(

I'm noticing it's happening on different interfaces, one day it might be one of the SATA ones, then an IDE one.

Could it be motherboard controller error ?

Oygle

---

### Post by oygle on 2009-04-01
Any clues please ?

---

### Post by Djzn.BR on 2010-05-14
I am getting these errors too.
The system gets stuck for 30 seconds randomly. Sometimes they have long gaps inbetween them.
It's hellish. 

They say it's a kernel bug. I remember that this started just after a kernel upgrade, the .31+ series, if I recollect right. I am almost getting another stock kernel and compiling it. This also may be related to AMD SB600 based motherboard owners. Quite painful to hear this, since all the HASSLE we go through with fglrx already.  

QUITE ANNOYING to death this is...
It's a SAMSUNG drive. Since millions are having these issues, I doubt this is a HDD hardware failure.


/dev/sda:

 Model=SAMSUNG, FwRev=JF100-19, SerialNo=S0V3J9AQ512165
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=34902, SectSize=554, ECCbytes=4
 BuffType=DualPortCache, BuffSize=8192kB, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=312581808
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-3,4,5,6,7

---

