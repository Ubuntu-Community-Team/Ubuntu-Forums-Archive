---
title: "hard drive suddenly unusably slow, problem with disk or updates? how to check?"
date: 2008-08-06
forum: Hardware
---

### Post by jetpeach on 2008-08-06
SOLVED: my hard drive was slowly failing, confirmed this using SMART testing. see the fourth post for instructions on testing a drive with smartctl.


i reboot my computer this evening and it suddenly took 10 minutes to boot. i tested:
sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   1418 MB in  2.00 seconds = 709.07 MB/sec
 Timing buffered disk reads:    **4 MB in  4.43 seconds = 924.11 kB/sec**

clearly something is seriously wrong - my other hard drive in the computer gets 
/dev/sdb:
 Timing cached reads:   1524 MB in  2.00 seconds = 762.42 MB/sec
 Timing buffered disk reads:  182 MB in  3.01 seconds =  60.45 MB/sec
so appears OK

when i try to change hdparm function (or even read them) i get an error
sudo hdparm -d /dev/sda
/dev/sda:
 HDIO_GET_DMA failed: Inappropriate ioctl for device

also, for c1, c2 or c3 get:
sudo hdparm -c1 /dev/sda
/dev/sda:
 setting 32-bit IO_support flag to 1
 HDIO_SET_32BIT failed: Invalid argument
 IO_support    =  0 (default)
16-bit)

i'm not sure if these errors were present before today though or if they actually are the reason for the slow down. the errors occur for both drives, but only the one has the bad performance...

the configuration is 2 PATA drives and a SATA cd-rom. it's been fine up until today, but i always install updates and i'm not sure if the hard drive is failing or if some update messed it up. could somebody tell me the best/easiest way to check if the hard drive is failing? would that be a likely explanation for the sudden performance drop? perhaps somebody else had the same thing happen after some recent updates? i recently switched to kde 4.1, i certainly hope this doesn't have anything to do with it...(i doubt it)

thanks for any help & advice you can give! 
jetpeach

output of other commands (for debugging)

sudo hdparm -i /dev/sda

/dev/sda:

 Model=ST3200822A                              , FwRev=3.01    , SerialNo=            4LJ34XF3
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=8192kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=390721968
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: ATA/ATAPI-6 T13 1410D revision 2:  ATA/ATAPI-1,2,3,4,5,6

**dmesg | grep ata**

[   21.943170] libata version 3.00 loaded.
[   22.672211] sata_nv 0000:00:08.0: version 3.5
[   22.672311] scsi0 : sata_nv
[   22.672351] scsi1 : sata_nv
[   22.672501] ata1: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 18
[   22.672504] ata2: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 18
[   23.136472] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   23.300410] ata1.00: ATAPI: ASUS    DRW-1814BLT, 1.04, max UDMA/66
[   23.472242] ata1.00: configured for UDMA/66
[   23.783843] ata2: SATA link down (SStatus 0 SControl 300)
[   23.798492] pata_amd 0000:00:06.0: version 0.3.10
[   23.798591] scsi2 : pata_amd
[   23.798634] scsi3 : pata_amd
[   23.799228] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[   23.799231] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[   24.136376] ata3.00: ATA-6: ST3200822A, 3.01, max UDMA/100
[   24.136381] ata3.00: 390721968 sectors, multi 16: LBA48
[   24.136569] ata3.01: ATA-7: HDT722516DLAT80, V43OA70A, max UDMA/133
[   24.136571] ata3.01: 321672960 sectors, multi 16: LBA48
[   24.152286] ata3.00: configured for UDMA/100
[   24.168247] ata3.01: configured for UDMA/133
[   24.168275] ata4: port disabled. ignoring.
[   24.579613] EXT3-fs: mounted filesystem with ordered data mode.
[   72.593031] EXT3-fs: mounted filesystem with ordered data mode.

part of lshw about IDE drives:
***-ide:0  **                                                                                                       
          description: IDE interface                                                                                 
          product: MCP61 IDE                                                                                         
          vendor: nVidia Corporation                                                                                 
          physical id: 6                                                                                             
          bus info: pci@0000:00:06.0                                                                                 
          version: a2                                                                                                
          width: 32 bits                                                                                             
          clock: 66MHz                                                                                               
          capabilities: ide bus_master cap_list                                                                      
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3 module=pata_amd                             
     
***-ide:1**                                                                                                         
          description: IDE interface                                                                                 
          product: MCP61 SATA Controller                                                                             
          vendor: nVidia Corporation                                                                                 
          physical id: 8                                                                                             
          bus info: pci@0000:00:08.0                                                                                 
          logical name: scsi0                                                                                        
          version: a2                                                                                                
          width: 32 bits                                                                                             
          clock: 66MHz                                                                                               
          capabilities: ide bus_master cap_list emulated                                                             
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3 module=sata_nv


THANKS AGAIN!

---

### Post by jetpeach on 2008-08-06
bump! hoping someone might still have some advice! thx

---

### Post by hotweiss on 2008-08-06
My hard drives performance went down the drain right before it failed. It might be time to back up your information.

---

### Post by jetpeach on 2008-08-06
well a little updating for anyone else who may have disk drive failure questions in the future - i ran some diagnostics on the drive by doing the following:

installed smartmontools (in repositories)

sudo smartctl -s on /dev/sda (where sda is your drive to test, this turns on SMART monitoring so you can get data about your drives errors/life)

sudo smartctl -t short /dev/sda (this runs a short test, let it finish for a minute)

sudo smartctl -a /dev/sda (this spits out a ton of data about the drive)

you could also just spit out the data on the drive that shows the test results:
sudo smartctl -l selftest /dev/sda

mine says:
=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       **Completed: read failure**       10%     15836         23054

Now when I ran the test and printed the output from my other, assumed healthy, drive, I got:
=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     22674         -

So it appears it truly is my hard drive dying! I will now see if I can warrenty the drive, although it might be too old...

Hope this helps anyone in the future with potential drive failure problems - I was unaware that drive performance would simply deteriorate (I expected errors like blue screens of death or something, but instead things just started taking a long long time...

Oh, to perform a long test on the drive (wasn't necessary for me) you can use 
sudo -t long /dev/sd[x] (where x is drive to be tested...)
and get the results with
sudo -l selftest /dev/sd[x]

jetpeach

---

### Post by krusbjorn on 2010-03-24
Thanks Jetpeach, this helped me.

---

