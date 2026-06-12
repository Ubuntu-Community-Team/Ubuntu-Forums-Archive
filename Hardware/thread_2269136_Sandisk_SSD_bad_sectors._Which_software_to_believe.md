---
title: "Sandisk SSD bad sectors. Which software to believe?"
date: 2015-03-13
forum: Hardware
---

### Post by marco.cognetti on 2015-03-13
Hello community!

I would like to have your feedback about a SSD disk (model X300s). I bought a new laptop few days ago running w8 (sucks!) with this SSD. Anyway, I run an Ubuntu 14.04 x64 live cd checking if everything is fine. 
Regarding the SSD, if I open the disks from the Ubuntu unity menu, it says that the disk is ok with 5 bad sectors (when I bought it they were 4). So, I investigated and the same number of bad sectors is shown by HDSentinel (from Windows). The expected life time is more than 1000 days. 

I contacted then SanDisk company, to check its opinion. They made me install the SanDisk SSD dashboard software ([http://kb.sandisk.com/app/answers/detail/a_id/15108/~/sandisk-ssd-dashboard-support-information](http://kb.sandisk.com/app/answers/detail/a_id/15108/~/sandisk-ssd-dashboard-support-information)) and I sent the report to them. They replied that there are no bad sectors and that HD sentinel as well as Ubuntu are not reliable for their model. In addition, the dashboard report that the status is 100% health.

I also tried [FONT=arial]sudo badblocks /dev/*[/FONT] with Ubuntu, saying me that there is no problem.

So, I'm really confused. Since the laptop is new, I have 10 days to decide if to return. I'm worried about the fact the bad sectors number are the same and they seem incresing (even if it is increased only by one). 

Any suggestion/comment? Which software do I have to believe?

Thank you,

Neostek

P.S. the report from HD sentinel

```
-- Physical Disk Information - Disk: #0: SanDisk SD7SB3Q256G1002 --


    Hard Disk Summary
   -------------------
    Hard Disk Number . . . . . . . . . . . . . . . . : 0
    Interface  . . . . . . . . . . . . . . . . . . . : S-ATA Gen3, 6 Gbps
    Disk Controller  . . . . . . . . . . . . . . . . : Intel(R) 8 Series Chipset Family SATA AHCI Controller (AHCI) [VEN: 8086, DEV: 8C03] Version: 13.1.0.1058, 5-2-2014
    Disk Location  . . . . . . . . . . . . . . . . . : Bus Number 4, Target Id 0, LUN 0
    Hard Disk Model ID . . . . . . . . . . . . . . . : SanDisk SD7SB3Q256G1002
    Firmware Revision  . . . . . . . . . . . . . . . : X2150000
    Hard Disk Serial Number  . . . . . . . . . . . . : 144784400204
    Total Size . . . . . . . . . . . . . . . . . . . : 244191 MB
    Power State  . . . . . . . . . . . . . . . . . . : Active
    Logical Drive(s) . . . . . . . . . . . . . . . . : C: [OS] D: [Data] 
    Current Temperature  . . . . . . . . . . . . . . : 39 \B0C
    Power On Time  . . . . . . . . . . . . . . . . . : 0 days, 14 hours
    Estimated Remaining Lifetime . . . . . . . . . . : more than 1000 days
    Health . . . . . . . . . . . . . . . . . . . . . : #################--- 87 % (Excellent)
    Performance  . . . . . . . . . . . . . . . . . . : #################### 100 % (Excellent)


    There are 5 bad sectors on the disk surface. The contents of these sectors were moved to the spare area.
    8 errors occured during data transfer. This may indicate problem of the device or with data/power cables. It is recommended to examine and replace the cables if possible. 
    At this point, warranty replacement of the disk is not yet possible, only if the health drops further.
    It is recommended to examine the log of the disk regularly. All new problems found will be logged there.
    The TRIM feature of the SSD is supported and enabled for optimal performance.
      No actions needed.


    ATA Information
   -----------------
    Hard Disk Cylinders  . . . . . . . . . . . . . . : 496149
    Hard Disk Heads  . . . . . . . . . . . . . . . . : 16
    Hard Disk Sectors  . . . . . . . . . . . . . . . : 63
    ATA Revision . . . . . . . . . . . . . . . . . . : ATA8-ACS.272
    Transport Version  . . . . . . . . . . . . . . . : SATA Rev 2.6
    Total Sectors  . . . . . . . . . . . . . . . . . : 500118192
    Bytes Per Sector . . . . . . . . . . . . . . . . : 512
    Multiple Sectors . . . . . . . . . . . . . . . . : 1
    Error Correction Bytes . . . . . . . . . . . . . : 0
    Unformatted Capacity . . . . . . . . . . . . . . : 244198 MB
    Maximum PIO Mode . . . . . . . . . . . . . . . . : 4
    Maximum Multiword DMA Mode . . . . . . . . . . . : 2
    Maximum UDMA Mode  . . . . . . . . . . . . . . . : 6 Gbps (6)
    Active UDMA Mode . . . . . . . . . . . . . . . . : 6 Gbps (6)
    Minimum Multiword DMA Transfer Time  . . . . . . : 120 ns
    Recommended Multiword DMA Transfer Time  . . . . : 120 ns
    Minimum PIO Transfer Time Without IORDY  . . . . : 120 ns
    Minimum PIO Transfer Time With IORDY . . . . . . : 120 ns
    ATA Control Byte . . . . . . . . . . . . . . . . : Valid
    ATA Checksum Value . . . . . . . . . . . . . . . : Valid


    Acoustic Management Configuration
   -----------------------------------
    Acoustic Management  . . . . . . . . . . . . . . : Not supported
    Acoustic Management  . . . . . . . . . . . . . . : Disabled
    Current Acoustic Level . . . . . . . . . . . . . : Default (00h)
    Recommended Acoustic Level . . . . . . . . . . . : Default (00h)


    ATA Features
   --------------
    Read Ahead Buffer  . . . . . . . . . . . . . . . : Supported, Enabled
    DMA  . . . . . . . . . . . . . . . . . . . . . . : Supported
    Ultra DMA  . . . . . . . . . . . . . . . . . . . : Supported
    S.M.A.R.T. . . . . . . . . . . . . . . . . . . . : Supported
    Power Management . . . . . . . . . . . . . . . . : Supported
    Write Cache  . . . . . . . . . . . . . . . . . . : Supported
    Host Protected Area  . . . . . . . . . . . . . . : Supported
    Advanced Power Management  . . . . . . . . . . . : Supported, Enabled
    Advanced Power Management Level  . . . . . . . . : Minimum power consumption without standby (128)
    Extended Power Management  . . . . . . . . . . . : Not supported
    Power Up In Standby  . . . . . . . . . . . . . . : Not supported
    48-Bit LBA Addressing  . . . . . . . . . . . . . : Supported
    Device Configuration Overlay . . . . . . . . . . : Supported
    IORDY Support  . . . . . . . . . . . . . . . . . : Supported
    Read/Write DMA Queue . . . . . . . . . . . . . . : Not supported
    NOP Command  . . . . . . . . . . . . . . . . . . : Not supported
    Trusted Computing  . . . . . . . . . . . . . . . : Not supported
    64-Bit World Wide ID . . . . . . . . . . . . . . : 01504CB467C14C9B
    Streaming  . . . . . . . . . . . . . . . . . . . : Not supported
    Media Card Pass Through  . . . . . . . . . . . . : Not supported
    General Purpose Logging  . . . . . . . . . . . . : Supported
    Error Logging  . . . . . . . . . . . . . . . . . : Supported
    CFA Feature Set  . . . . . . . . . . . . . . . . : Not supported
    CFast Device . . . . . . . . . . . . . . . . . . : Not supported
    Long Physical Sectors (1)  . . . . . . . . . . . : Not supported
    Long Logical Sectors . . . . . . . . . . . . . . : Not supported
    Write-Read-Verify  . . . . . . . . . . . . . . . : Not supported
    NV Cache Feature . . . . . . . . . . . . . . . . : Not supported
    NV Cache Power Mode  . . . . . . . . . . . . . . : Not supported
    NV Cache Size  . . . . . . . . . . . . . . . . . : Not supported
    Free-fall Control  . . . . . . . . . . . . . . . : Not supported
    Free-fall Control Sensitivity  . . . . . . . . . : Not supported
    Nominal Media Rotation Rate  . . . . . . . . . . : Non-rotating Media (SSD)


    SSD Features
   --------------
    Data Set Management  . . . . . . . . . . . . . . : Supported
    TRIM Command . . . . . . . . . . . . . . . . . . : Supported
    Deterministic Read After TRIM  . . . . . . . . . : Supported
    Operating System TRIM Function . . . . . . . . . : Supported, Enabled


    S.M.A.R.T. Details
   --------------------
    Off-line Data Collection Status  . . . . . . . . : Never Started
    Self Test Execution Status . . . . . . . . . . . : Test Is In Progress, 30 % completed
    Total Time To Complete Off-line Data Collection  : 0 seconds
    Execute Off-line Immediate . . . . . . . . . . . : Supported
    Abort/restart Off-line By Host . . . . . . . . . : Not supported
    Off-line Read Scanning . . . . . . . . . . . . . : Not supported
    Short Self-test  . . . . . . . . . . . . . . . . : Supported
    Extended Self-test . . . . . . . . . . . . . . . : Supported
    Conveyance Self-test . . . . . . . . . . . . . . : Not supported
    Selective Self-Test  . . . . . . . . . . . . . . : Not supported
    Save Data Before/After Power Saving Mode . . . . : Supported
    Enable/Disable Attribute Autosave  . . . . . . . : Supported
    Error Logging Capability . . . . . . . . . . . . : Supported
    Short Self-test Estimated Time . . . . . . . . . : 2 minutes
    Extended Self-test Estimated Time  . . . . . . . : 10 minutes
    Last Short Self-test Result  . . . . . . . . . . : Never Started
    Last Short Self-test Date  . . . . . . . . . . . : Never Started
    Last Extended Self-test Result . . . . . . . . . : Never Started
    Last Extended Self-test Date . . . . . . . . . . : Never Started


    Security Mode
   ---------------
    Security Mode  . . . . . . . . . . . . . . . . . : Supported
    Security Erase . . . . . . . . . . . . . . . . . : Supported
    Security Erase Time  . . . . . . . . . . . . . . : 2 minutes
    Security Enhanced Erase Feature  . . . . . . . . : Supported
    Security Enhanced Erase Time . . . . . . . . . . : 18 minutes
    Security Enabled . . . . . . . . . . . . . . . . : No
    Security Locked  . . . . . . . . . . . . . . . . : No
    Security Frozen  . . . . . . . . . . . . . . . . : Yes
    Security Counter Expired . . . . . . . . . . . . : No
    Security Level . . . . . . . . . . . . . . . . . : High


    Serial ATA Features
   ---------------------
    S-ATA Compliance . . . . . . . . . . . . . . . . : Yes
    S-ATA I Signaling Speed (1.5 Gps)  . . . . . . . : Supported
    S-ATA II Signaling Speed (3 Gps) . . . . . . . . : Supported
    S-ATA Gen3 Signaling Speed (6 Gps) . . . . . . . : Supported
    Receipt Of Power Management Requests From Host . : Supported
    PHY Event Counters . . . . . . . . . . . . . . . : Supported
    Non-Zero Buffer Offsets In DMA Setup FIS . . . . : Not supported
    DMA Setup Auto-Activate Optimization . . . . . . : Supported, Enabled
    Device Initiating Interface Power Management . . : Supported, Enabled
    In-Order Data Delivery . . . . . . . . . . . . . : Not supported
    Asynchronous Notification  . . . . . . . . . . . : Not supported
    Software Settings Preservation . . . . . . . . . : Supported, Enabled
    Native Command Queuing (NCQ) . . . . . . . . . . : Supported
    Queue Length . . . . . . . . . . . . . . . . . . : 32


    S.M.A.R.T.
   ------------
No.  Attribute                Thre.. Value  Worst  Data                Status                   Flags                                                  
5    Retired Block Count      0      100    100    000000000005        OK (Always passing)      Self Preserving, Event Count, Statistical              
9    Power On Time Count      0      14     100    00000000000E        OK (Always passing)      Self Preserving, Event Count, Statistical              
12   Drive Power Cycle Count  0      100    100    000000000057        OK (Always passing)      Self Preserving, Event Count, Statistical              
166  Min W/E Cycle            0      100    100    000000000001        OK (Always passing)      Self Preserving, Event Count, Statistical              
167  Max Bad Block/Die        0      100    100    00000000003D        OK (Always passing)      Self Preserving, Event Count, Statistical              
168  Maximum Erase Cycle      0      100    100    000000000008        OK (Always passing)      Self Preserving, Event Count, Statistical              
169  Total Bad Block          0      100    100    0000000002ED        OK (Always passing)      Self Preserving, Event Count, Statistical              
171  Program Fail Count       0      100    100    000000000001        OK (Always passing)      Self Preserving, Event Count, Statistical              
172  Erase Fail Count         0      100    100    000000000000        OK (Always passing)      Self Preserving, Event Count, Statistical              
173  Average Erase Cycle      0      100    100    000000000001        OK (Always passing)      Self Preserving, Event Count, Statistical              
174  Unexpected Power Loss .. 0      100    100    000000000009        OK (Always passing)      Self Preserving, Event Count, Statistical              
184  Error Correction Count   0      100    100    000000000000        OK (Always passing)      Self Preserving, Event Count, Statistical              
187  Reported Uncorrectable.. 0      100    100    000000000000        OK (Always passing)      Self Preserving, Event Count, Statistical              
188  Command Timeout Count    0      100    100    000000000000        OK (Always passing)      Self Preserving, Event Count, Statistical              
194  Current Temperature      0      61     46     002E00170027        OK (Always passing)      Self Preserving, Statistical                           
199  Ultra ATA CRC Error Co.. 0      100    100    000000000000        OK (Always passing)      Self Preserving, Event Count, Statistical              
212  SATA PHY Error           0      100    100    000000000000        OK (Always passing)      Self Preserving, Event Count, Statistical              
230  Percentage Total P/E C.. 0      100    100    000000000003        OK (Always passing)      Self Preserving, Event Count, Statistical              
232  Spare Blocks Remaining   4      100    100    000000000063        OK                       Self Preserving, Event Count, Statistical, Critical    
233  Total GB Written to NAND 0      100    100    000000000150        OK (Always passing)      Self Preserving, Event Count, Statistical              
241  Total Host Writes        0      253    253    000000000109        OK (Always passing)      Self Preserving, Event Count                           
242  Total Host Reads         0      253    253    00000000008B        OK (Always passing)      Self Preserving, Event Count                           
244  ECC Cumulative Thresho.. 0      0      100    000000000000        OK (Always passing)      Self Preserving, Event Count, Statistical              


    Transfer Rate Information
   ---------------------------
    Total Data Read  . . . . . . . . . . . . . . . . : 1,193 MB,  4,826 MB since installation  (3/12/2015)
    Total Data Write . . . . . . . . . . . . . . . . : 375 MB,  1,381 MB since installation
    Average Reads Per Day  . . . . . . . . . . . . . : 4,826.00 MB
    Average Writes Per Day . . . . . . . . . . . . . : 1,381.00 MB
    Current Transfer Rate  . . . . . . . . . . . . . : 65 KB/s
    Maximum Transfer Rate  . . . . . . . . . . . . . : 109545 KB/s
    Current Read Rate  . . . . . . . . . . . . . . . : 0 KB/s
    Current Write Rate . . . . . . . . . . . . . . . : 65 KB/s
    Current Disk Activity  . . . . . . . . . . . . . : 0 %






  -- Physical Disk Information - Disk: #1: Generic USB Flash Disk --


    Hard Disk Summary
   -------------------
    Hard Disk Number . . . . . . . . . . . . . . . . : 1
    Interface  . . . . . . . . . . . . . . . . . . . : USB
    Vendor Information . . . . . . . . . . . . . . . : VID: 048D, PID: 1172
    Disk Controller  . . . . . . . . . . . . . . . . : Intel(R) USB 3.0 eXtensible Host Controller - 0100 (Microsoft) (USB 3.0) [VEN: 8086, DEV: 8C31] Version: 6.3.9600.17393, 10-6-2014
    Hard Disk Model ID . . . . . . . . . . . . . . . : Generic USB Flash Disk
    Firmware Revision  . . . . . . . . . . . . . . . : 0.00
    Hard Disk Serial Number  . . . . . . . . . . . . : ITEu10011172A3CA
    Total Size . . . . . . . . . . . . . . . . . . . : 7679 MB
    Power State  . . . . . . . . . . . . . . . . . . : Active
    Logical Drive(s) . . . . . . . . . . . . . . . . : F: [] 
    Current Temperature  . . . . . . . . . . . . . . : ?
    Health . . . . . . . . . . . . . . . . . . . . . : ? (Unknown)
    Performance  . . . . . . . . . . . . . . . . . . : ? (Unknown)


    Properties
   ------------
    Vendor Information . . . . . . . . . . . . . . . : ?
    Status . . . . . . . . . . . . . . . . . . . . . : OK
    Version  . . . . . . . . . . . . . . . . . . . . : 4
    Device Type  . . . . . . . . . . . . . . . . . . : Disk
    ASC  . . . . . . . . . . . . . . . . . . . . . . : 0
    ASCQ . . . . . . . . . . . . . . . . . . . . . . : 0


    SCSI Information
   ------------------
    Removable  . . . . . . . . . . . . . . . . . . . : Supported
    Failure Prediction . . . . . . . . . . . . . . . : Not supported
    Failure Prediction . . . . . . . . . . . . . . . : Disabled


    Hard Disk Test
   ----------------
    Short Self-test  . . . . . . . . . . . . . . . . : Not supported
    Extended Self-test . . . . . . . . . . . . . . . : Not supported


    Transfer Rate Information
   ---------------------------
    Real time performance monitoring is not supported on this disk.
```

---

### Post by tgalati4 on 2015-03-13
SSD controllers are quite complicated.  Data is written to large flash memory blocks even if only one bit changes in a block.  All of this is hidden to the user.  It's possible that the SMART parameters record this behavior.  So yes, the controller had to move some data around to get around blocks that were failing or otherwise not within specification.

Personally, I think that manufacturers take advantage of the Windows OS installation getting balled up over time.  So when Windows fails to behave properly, the course of action is to reinstall--to a clean, Like New, experience.  Linux users know better.  

So your drive has no current badblocks, but the controller has had to take action.  Will this happen again.  Most likely.  Will it degrade before Ubuntu Linux needs reinstallation?  Likely.  Most installs will last more than 1000 days.  Windows, not so much.

It's possible that there is a bug in reading SMART parameters from an SSD, but I doubt it.  It seems too specific to this case.  SanDisk's response is typical: "Only certified with Windows using our proprietary tools."

If you find other things that you don't like about the laptop in 10 days, then return it.  The disk should certainly last that long.

---

### Post by marco.cognetti on 2015-03-13
Thank you for your reply. The laptop seems perfect for other things (obviously, I will test it in the next few days). 

So you suggest me that the disk is fine, I have to not worry about it. Did I understand it correctly? It might be possible that Ubuntu sets with bad sectors due to unexpected shutdown of Windows? I mean a couple of times, I hold the power button since it was taking too long to shut down.

In addition, with an SSD, do you think that it is better to shut down Windows with a command (shutdown /t /s 0, i.e. without faststartup disabled), I mean completely shutdown, or use the hybrid shutdown that w8 provide by standard (with faststartup disabled)?

Thank you,
Neostek

---

### Post by tgalati4 on 2015-03-13
I don't use Windows anymore, so I can't comment, but shutting down with the hard power button will cause some files not to get written.  This may or may not result in disk errors.

Never use the hard button shutdown in Linux if you can avoid it.  Always try the Control-Alt-Shift-SysRq  and R-E-I-S-U-B to shut down a kernel panic or freeze.  The hard button is a last resort.  Windows taking forever to shut down is a feature of the operating system.

---

### Post by Mark Phelps on 2015-03-13
FastStartup in Win8 is simply a new form of hibernation which causes all the filesystems open when Windows is "Shut Down" to remain mounted.

Disabling FastStartup disables the default hibernation.  But, since you use an SSD, the speed improvement in boot time with FastStartup enabled is likely very small.  I would recommend permanently disabling it.

Understand, though, if you use "restart" to turn off Win8, that automatically enables hibernation, even if FastStartup is disabled.  So. always use "Shut Down".

---

### Post by marco.cognetti on 2015-03-13
Thank you for your comments. What do you suggest then? I usually do not use Windows (I'm a pure Ubuntu user) and that's the reason I tell you this.

Do I have to be worried about the 5 bad sectors? Or just badblocks is fine? Other things I can try to check if it is an healthy SSD?

Thank you,
Neostek

---

### Post by tgalati4 on 2015-03-13
Use it for a year.  If it fails then you will know.  Right now it is OK.  Tomorrow probably OK.  I would not recommend stress-testing the SSD like you would with a spinning hard disk.  That will just wear out the flash memory quicker.

---

### Post by weatherman2 on 2015-03-13
You should be making regular backups whether there are 0 "bad sectors" showing or 5.  Hard drives and SSDs can fail suddenly, without warning.

I would monitor the SSD's health regularly for a few weeks.  If the number of "bad sectors" does not increase, I would stop worrying about it but continue a regular backup scheme.  If the number of "bad sectors" continues to rise, then I would worry.

---

### Post by efflandt on 2015-03-14
Drives automatically reserve some space to automatically transparently remap good sectors in place of bad sectors regardless of OS. So detailed diagnostics that shows in inner workings of the drive that it has 4 or 5 bad blocks that were mapped out is not an issue and would not even be seen by Windows chkdsk or badblocks in Linux. When you run our of the hidden reserve space and actually start seeing badblocks is when it is time to be concerned because at that point it can only get worse. Even regular hard drives are generally not replaced under warranty unless all of the error sites are used up or something else is wrong with the drive (at least a rapidly increasing number of remapped errors).

I recently installed a Crucial mSATA SSD card in my gaming laptop for Ubuntu and something I read about setting up Ubuntu on SSD said to leave 7% of the drive unallocated, so as the flash wears out and is retired it does not get in the way. Although, that may have been from when SSD drives were smaller and I left a lower percent unallocated (unformatted) on the 512 GB mSATA because I think the manufacturer may have reserved some space for flash eventually wearing out and I do not use my laptop that frequently.

---

### Post by Mark Phelps on 2015-03-14
I had a brand new Kingston Hyper-X SSD start failing with filesystem corruptions on a daily basis.  All the tests I ran, including the SMART utility provided by Kingston, indicated the drive was OK, but nonetheless, the OS kept failing on a daily basis.  Suspecting something in the OS, I imaged it off and "restored" it to a spare hard drive -- which then worked fine for two weeks with no problems at all.  I then imaged off the hard drive and "restored" it to the Kingston, and upon the first reboot with the Kingston, encountered filesystem corruption -- again!

Fortunately, Kingston agreed to replace the drive, and with the replacement drive, I have had no problems at all.

I would see if you can get a replacement drive.

---

### Post by marco.cognetti on 2015-03-15
Thank you for your replies.

New update: both Ubuntu and HD sentinel says there are 6 (not 5 anymore) bad sectors but if I run sudo badblocks /dev/sda* -nvp there is no block. 

What's going on here?

I never had problem such as I/O input error or blue screen from Windows. I'm only concerned that I will have problems in the next future about this SSD. 
My question is: is HD sentinel and Ubuntu reliable? Or do I have to trust SSD sandisk dashboard that says everything is fine?

Thank you,

Neostek

---

### Post by Mark Phelps on 2015-03-16
IF it were my SSD and bad sectors were reported, I would look into getting a replacement -- if the warranty is still in effect.  Some SSDs are warrantied for three years -- don't know about SanDisk.

---

### Post by marco.cognetti on 2015-03-16
The only problem is that I have to return the entire laptop in case. The increasing sector appears after I run 
sudo badblocks -nvs 
on the hard drive. Should it be that? 
In any case, I'm confused since it says there is no bad block but there are 6 bad sectors. I recall it is a SSD. 
Is there any way to properly test it or to check if there are problems with the motherboard?

Thank you,
Neostek

---

### Post by tgalati4 on 2015-03-16
You should not use the -n switch since that is reading and writing to every block on the SSD which wears it out slightly.  So yes, if flash memory is wearing out, you will get an increasing number of bad sectors.  It could be that 6 sectors are slugglish--slow to read or that they were reallocated to new sectors so you do have 6 sectors that had to be moved, but you have several hundered (or thousand) in reserve.  This is transparent to the user.  You don't see it until you run out of reserve sectors--when the SMART paramter runs down to 10% (out of 100).

---

### Post by marco.cognetti on 2015-03-16
Ok it means that, when I run the badblocks with -n option active I write also on the SSD, so the increased number is due to that. 

Do you think that the increased number is then normal and I should not worry about that?
I recall that the laptop is new (one week of life), so that is the reason for which I'm worried even if there are few reallocated sector number (you said it is "[COLOR=#000000]flash memory is wearing out[/COLOR]", already?).

Thank you, 
Neostek

---

### Post by Mark Phelps on 2015-03-16
You really shouldn't have any bad sectors on a new drive.  If you run this for a while and monitor the SMART settings and the SMART parameter is not running down, you should be OK.  A recently published long-term test of SSD survivability showed that failure rates didn't become noticable until around the 100TB write timeframe.  

Still, if you can get the drive exchanged, you should check into that.

---

### Post by marco.cognetti on 2015-03-16
Well, Ubuntu says they are bad sectors...what the Windows tells is that they are "reallocated sectors", I do not know if this makes a difference. Do you suggest any software to get the SMART parameter? And which parameter do I have to look with particular attention?

Anyway, sandisk says that since it is a pre-built SSD (that come with the laptop), I have to talk with ASUS, for technical services. I'm afraid ASUS will require the entire laptop for testing and I'm afraid it will just send it me again since it is not broken.

Thank you,
Neostek

---

### Post by marco.cognetti on 2015-03-17
I'm wondering if there is a difference between bad sectors and reallocated sectors (I'm pretty sure there is, the latter can be recovered IMHO)....
but why Ubuntu mark whose sectors as bad sectors, while the SanDisk SSD dashboard as reallocated? Is there a way to be able that Ubuntu checks if they are reallocated sectors or bad sectors? 

Suggestions?

Thank you,
Neostek

---

### Post by tgalati4 on 2015-03-17
If the number of bad sectors is 6 and the number of relocated sectors is 6 then one could conclude that Ubuntu treats relocated sectors are bad sectors.  But your system works because those bad sectors were relocated and are now readable.

---

### Post by marco.cognetti on 2015-03-18
Thank you for your reply. 
Does it mean that Ubuntu will never reuse those sectors since it treats as bad sectors?
Is that normal for a new drive?

Thank you,
Neostek

---

### Post by tgalati4 on 2015-03-18
I don't know where the list of bad blocks is kept.  You can see the number of reserved blocks that are kept for system use (typically 5 to 7%) for housekeeping purposes.

tgalati4@Mint17 ~ $ sudo dumpe2fs /dev/sda1 | grep Reserved
dumpe2fs 1.42.9 (4-Feb-2014)
**Reserved block count:     931468**

The SSD controller handles relocation of bad blocks at a low level.  You would need a special utility from the manufacturer to read this.  It is different for each company that makes SSD.

---

### Post by marco.cognetti on 2015-03-18
I have for that 
Reserved block counts: 1517478

I also run the manufacturer tool (in Windows) for the SSD. It says that there are 6 reallocated sector counts as well. There is no mention on bad sectors.

I also run smartctrl -a /dev/sda to check it. 
ID 5 says the reallocated sectors are 6
ID 232 Available_Reservd_Space 0x0033   100   100   004    Pre-fail  Always       -       99
ID 233 Media_Wearout_Indicator 0x0032   100   100   ---    Old_age   Always       -       1388 

Are they good for an healthy SSD?

```
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Device Model:     SanDisk SD7SB3Q256G1002
Serial Number:    144784400204
LU WWN Device Id: 5 001b44 cc1679b4c
Firmware Version: X2150000
User Capacity:    256,060,514,304 bytes [256 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    Solid State Device
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ACS-2 T13/2015-D revision 3
SATA Version is:  SATA >3.1, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Wed Mar 18 07:25:04 2015 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)   Offline data collection activity
               was never started.
               Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)   The previous self-test routine completed
               without error or no self-test has ever 
               been run.
Total time to complete Offline 
data collection:       (    0) seconds.
Offline data collection
capabilities:           (0x11) SMART execute Offline immediate.
               No Auto Offline data collection support.
               Suspend Offline collection upon new
               command.
               No Offline surface scan supported.
               Self-test supported.
               No Conveyance Self-test supported.
               No Selective Self-test supported.
SMART capabilities:            (0x0003)   Saves SMART data before entering
               power-saving mode.
               Supports SMART auto save timer.
Error logging capability:        (0x01)   Error logging supported.
               General Purpose Logging supported.
Short self-test routine 
recommended polling time:     (   2) minutes.
Extended self-test routine
recommended polling time:     (  10) minutes.

SMART Attributes Data Structure revision number: 4
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  5 Reallocated_Sector_Ct   0x0032   100   100   ---    Old_age   Always       -       6
  9 Power_On_Hours          0x0032   023   100   ---    Old_age   Always       -       23
 12 Power_Cycle_Count       0x0032   100   100   ---    Old_age   Always       -       107
166 Unknown_Attribute       0x0032   100   100   ---    Old_age   Always       -       1
167 Unknown_Attribute       0x0032   100   100   ---    Old_age   Always       -       61
168 Unknown_Attribute       0x0032   100   100   ---    Old_age   Always       -       41
169 Unknown_Attribute       0x0032   100   100   ---    Old_age   Always       -       750
171 Unknown_Attribute       0x0032   100   100   ---    Old_age   Always       -       2
172 Unknown_Attribute       0x0032   100   100   ---    Old_age   Always       -       0
173 Unknown_Attribute       0x0032   100   100   ---    Old_age   Always       -       5
174 Unknown_Attribute       0x0032   100   100   ---    Old_age   Always       -       9
184 End-to-End_Error        0x0032   100   100   ---    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   ---    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   ---    Old_age   Always       -       0
194 Temperature_Celsius     0x0022   059   049   ---    Old_age   Always       -       41 (Min/Max 21/49)
199 UDMA_CRC_Error_Count    0x0032   100   100   ---    Old_age   Always       -       0
212 Unknown_Attribute       0x0032   100   100   ---    Old_age   Always       -       0
230 Unknown_SSD_Attribute   0x0032   100   100   ---    Old_age   Always       -       16
232 Available_Reservd_Space 0x0033   100   100   004    Pre-fail  Always       -       99
233 Media_Wearout_Indicator 0x0032   100   100   ---    Old_age   Always       -       1388
241 Total_LBAs_Written      0x0030   253   253   ---    Old_age   Offline      -       756
242 Total_LBAs_Read         0x0030   253   253   ---    Old_age   Offline      -       1024
244 Unknown_Attribute       0x0032   000   100   ---    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%        22         -
# 2  Extended offline    Completed without error       00%        21         -
# 3  Extended offline    Completed without error       00%        20         -
# 4  Extended offline    Completed without error       00%        17         -
# 5  Short offline       Aborted by host               00%        15         -
# 6  Short offline       Completed without error       00%        14         -
# 7  Short offline       Aborted by host               00%        14         -
# 8  Extended offline    Completed without error       00%        14         -
# 9  Extended offline    Aborted by host               00%        14         -
#10  Extended offline    Completed without error       00%         9         -

Selective Self-tests/Logging not supported
```

What do you think? Is that an healthy SSD? (recall it is new)
Neostek

---

### Post by tgalati4 on 2015-03-18
It looks OK.

---

### Post by marco.cognetti on 2015-03-18
Sorry what the [COLOR=#000000]Reserved block counts: 1517478 are? he number of block my SSD can substitute (now 6)?

Thank you,
Neostek[/COLOR]

---

### Post by tgalati4 on 2015-03-19
No, that is the reserved blocks when you run out of disk space.  That allows the system to keep running while the file system figures out which processes to kill.  You can increase or decrease this value but it is usually 5% by default.  I don't know how to find the actual reserved blocks for bad sectors on the SanDisk SSD.  Perhaps send an email to SanDisk and explain your situation.

---

### Post by marco.cognetti on 2015-03-19
SanDisk says that a reallocated sector does not mean for sure that it is a damaged sector (it could be also a slow sector moved for security reason). But they did not provide me a standard trend for my SSD for this number neither which is the highest number after which I should be worried about. This is not so professional in my opinion. Anyway, from the SSD SanDisk Dashboard the remaining life is at 100%. So, I will use the laptop and check if this number increases over time. 

My worry is just that the SSD is really new and this is my first time with an SSD. So I have no idea about the trend it should have. I guess the first sectors was due to hard shutdown I did in Windows (so it registered read/write errors). What I did not get is why it increases when I launched
sudo badblocks -nvp
I know it is enabled the writing option but the SSD is new, so the flash memory can not wearing out yet, right?

Thank you,
Neostek

---

