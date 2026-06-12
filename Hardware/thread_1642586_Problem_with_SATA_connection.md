---
title: "Problem with SATA connection"
date: 2010-12-10
forum: Hardware
---

### Post by masterkorp on 2010-12-10
Hello, recently i am experiencing problems with my system.
My systems becomes very slow and some apps freeze (happens randomly).

I checked my logs, and there are problems with my SATA connection.
Can be the motherboard? Or the hard drive ? Or even ubuntu.
I don't know how to interpert this log very good.

Here it is: 

```

[ 5170.609707] ata1.00: status: { DRDY ERR }
[ 5170.609710] ata1.00: error: { ICRC ABRT }
[ 5170.609718] ata1: hard resetting link
[ 5171.111323] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 5171.150343] ata1.00: configured for UDMA/33
[ 5171.150366] ata1: EH complete
[ 5171.186071] ata1.00: exception Emask 0x10 SAct 0x0 SErr 0x400100 action 0x6
[ 5171.186076] ata1.00: BMDMA stat 0x26
[ 5171.186080] ata1: SError: { UnrecovData Handshk }
[ 5171.186084] ata1.00: failed command: WRITE DMA
[ 5171.186091] ata1.00: cmd ca/00:e0:08:a9:5d/00:00:00:00:00/eb tag 0 dma 114688 out
[ 5171.186093]          res 51/84:a1:47:a9:5d/84:01:09:00:00/eb Emask 0x30 (host bus error)
[ 5171.186096] ata1.00: status: { DRDY ERR }
[ 5171.186099] ata1.00: error: { ICRC ABRT }
[ 5171.186107] ata1: hard resetting link
[ 5171.700065] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 5171.741604] ata1.00: configured for UDMA/33
[ 5171.741626] ata1: EH complete
[ 5173.512337] ata1.00: exception Emask 0x10 SAct 0x0 SErr 0x400100 action 0x6
[ 5173.512341] ata1.00: BMDMA stat 0x26
[ 5173.512344] ata1: SError: { UnrecovData Handshk }
[ 5173.512347] ata1.00: failed command: WRITE DMA EXT
[ 5173.512352] ata1.00: cmd 35/00:70:30:7f:a9/00:03:03:00:00/e0 tag 0 dma 450560 out
[ 5173.512353]          res 51/84:e0:c0:81:a9/84:00:03:00:00/e0 Emask 0x30 (host bus error)
[ 5173.512356] ata1.00: status: { DRDY ERR }
[ 5173.512357] ata1.00: error: { ICRC ABRT }
[ 5173.512365] ata1: hard resetting link
[ 5174.030064] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 5174.071587] ata1.00: configured for UDMA/33
[ 5174.071606] ata1: EH complete
[ 5180.422111] ata1.00: exception Emask 0x10 SAct 0x0 SErr 0x400100 action 0x6
[ 5180.422117] ata1.00: BMDMA stat 0x26
[ 5180.422121] ata1: SError: { UnrecovData Handshk }
[ 5180.422125] ata1.00: failed command: WRITE DMA
[ 5180.422132] ata1.00: cmd ca/00:08:18:42:79/00:00:00:00:00/ee tag 0 dma 4096 out
[ 5180.422134]          res 51/84:01:1f:42:79/84:00:03:00:00/ee Emask 0x30 (host bus error)
[ 5180.422137] ata1.00: status: { DRDY ERR }
[ 5180.422140] ata1.00: error: { ICRC ABRT }
[ 5180.422148] ata1: hard resetting link
[ 5180.930096] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 5180.978157] ata1.00: configured for UDMA/33
[ 5180.978170] ata1: EH complete
[ 5181.143700] ata1.00: exception Emask 0x10 SAct 0x0 SErr 0x400100 action 0x6
[ 5181.143705] ata1.00: BMDMA stat 0x26
[ 5181.143707] ata1: SError: { UnrecovData Handshk }
[ 5181.143711] ata1.00: failed command: WRITE DMA
[ 5181.143715] ata1.00: cmd ca/00:08:50:8a:a9/00:00:00:00:00/e3 tag 0 dma 4096 out
[ 5181.143716]          res 51/84:00:57:8a:a9/84:00:03:00:00/e3 Emask 0x30 (host bus error)
[ 5181.143719] ata1.00: status: { DRDY ERR }
[ 5181.143720] ata1.00: error: { ICRC ABRT }
[ 5181.143727] ata1: hard resetting link
[ 5181.661325] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 5181.711578] ata1.00: configured for UDMA/33
[ 5181.711591] ata1: EH complete
[ 5189.238774] ata1.00: exception Emask 0x10 SAct 0x0 SErr 0x400100 action 0x6
[ 5189.238780] ata1.00: BMDMA stat 0x26
[ 5189.238784] ata1: SError: { UnrecovData Handshk }
[ 5189.238788] ata1.00: failed command: WRITE DMA
[ 5189.238795] ata1.00: cmd ca/00:70:70:91:a9/00:00:00:00:00/e3 tag 0 dma 57344 out
[ 5189.238796]          res 51/84:10:d0:91:a9/84:00:03:00:00/e3 Emask 0x30 (host bus error)
[ 5189.238800] ata1.00: status: { DRDY ERR }
[ 5189.238802] ata1.00: error: { ICRC ABRT }
[ 5189.238810] ata1: hard resetting link
[ 5189.740062] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[ 5189.781582] ata1.00: configured for UDMA/33
[ 5189.781596] ata1: EH complete

```

Can someone point me in the right direction ?

---

### Post by HankB on 2010-12-10
The next thing I'd look at is the SMART information in the hard drive. You can view this by installing smartmontools. Use Ubuntu Software Center or:

```
sudo apt-get install smartmontools
```

Then examine the drive with:

```
sudo smartctl -a /dev/sda
```

Among the results will be something that looks like:
```
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       1
  3 Spin_Up_Time            0x0027   185   182   021    Pre-fail  Always       -       1733
  4 Start_Stop_Count        0x0032   096   096   000    Old_age   Always       -       4146
**  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0**
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   083   083   000    Old_age   Always       -       12597
 10 Spin_Retry_Count        0x0033   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       162
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       36
193 Load_Cycle_Count        0x0032   195   195   000    Old_age   Always       -       15953
194 Temperature_Celsius     0x0022   109   099   000    Old_age   Always       -       38
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0009   100   253   051    Pre-fail  Offline      -       0
```

The Reallocated_Sector_Ct is the one that I watch. If it is growing, the drive is in the process of failing. 

This command may also report other errors that the drive is experiencing. Post anything that looks suspicious and hopefully someone will be able to provide help.

NB, I recently had an IBM Deskstar (Deathstar?) start to go bad after about 7 years of operation. It did not reveal anything I found notable in the SMART diagnostics.

Now would be a real good time to make sure your backups are current!

Good luck!

---

### Post by masterkorp on 2010-12-10
Thanks man, i totally forgot of checking S.M.A.R.T!. I just checked the disk surface with [testdisk]("http://www.cgsecurity.org/wiki/TestDisk").
Well i checked and no problems whit **Reallocated_Sector_Ct** but i did have additional info about errors.
Here it is:

```

Error 781 occurred at disk power-on lifetime: 3764 hours (156 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 51 c0 e0 c7 a9 e3  Error: ABRT at LBA = 0x03a9c7e0 = 61458400

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ca 00 c0 e0 c7 a9 e3 00      04:07:04.875  WRITE DMA
  ca 00 08 10 67 31 ee 00      04:07:04.875  WRITE DMA
  ca 00 08 90 66 31 ee 00      04:07:04.875  WRITE DMA
  ca 00 08 d8 65 31 ee 00      04:07:04.875  WRITE DMA
  ca 00 08 f8 64 31 ee 00      04:07:04.875  WRITE DMA

```
This was happened 781 times until now!
I checked the disk health with smartctl -H and it was passed.

I am ruining a long test right now, i will give info on that.

Can you point me in right direction ?
Does Samgung (my disk malefactor) have this documented ?

Thanks already.

---

### Post by HankB on 2010-12-11
> **masterkorp said:**
> 
This was happened 781 times until now!
...

Can you point me in right direction ?
Does Samgung (my disk malefactor) have this documented ?

That seems like it would indicate what the problem is. Unfortunately I don't know what the various codes mean.

I would send a copy of that to Samsung to see if they can identify the problem.

Another thing to do is to make sure cables are firmly attached and so on. I would be thinking about replacing the disk at this point but I cannot rule out a cabling or power supply issue.

You might also look for a computer hardware oriented forum where you might find someone who can interpret those codes or will recognize the problem. It might also be worth googling the drive ID to see if it is a common problem with that model (like the problems common with the Deathstars.)

---

### Post by WinRiddance on 2010-12-11
> Hello, recently i am experiencing problems with my system.
My systems becomes very slow and some apps freeze (happens randomly).In particular on desktop systems, what you describe is a classic example of cooling fans that are either beginning to fail or dirt clogging up the system which causes the CPU to run a lot hotter. You'd be amazed at the kind of dirt that finds itself on those cooling fans and heat sinks, especially if the system is near or on the carpet, people are smoking around the system, and so on. The symptoms/failures would be varied between Windows and Ubuntu for the simple reason that each of them uses CPU and memory resources differently.

I've built, repaired, and upgraded literally hundreds of computers, probably at least 300 of them, and have never seen a disk drive that failed with less than 4 years of constant use ... unless something physical happened to damage the disk (falling to the ground, PC getting hit by a flying football, no kidding,). I've worked on power user and server machines that run constantly, 24 X 7 without ever being powered down, and hard disks never failed. People are freaking out way more than needed about hard disk issues while not looking at more appropriate areas of concern.

Proper cooling and cleanliness are the keys to a smoothly running computer. That's why big companies keep their servers in air conditioned enclosures. A lot of laptops can get pretty clogged up with dirt and dust too, especially if it spends a lot of time on the couch, your lap, the bed, and so on. Check your cooling fans and heat sink before you do anything else. Get a small paintbrush to clean all of the crud out. That's very easy to do. How old is this computer? Is it a laptop or a desktop PC unit? Which version of Ubuntu are you running on this system? Failing memory could cause problems like this too, but it's pretty unlikely.

**BTW:**  I always receive error messages with testdisk and other MBR utilities but as long as your disk health checks out with the disk utility, I really wouldn't worry about it at all. Matter of fact, just recently I had to do some data recovery from two different disks, one of them a refurbished 3+ year old generic ATA drive. Both disks are perfectly fine and disk health checks out 100% okay, even though testdisk still shows errors.

---

### Post by masterkorp on 2010-12-11
> **WinRiddance said:**
> In particular on desktop systems, what you describe is a classic example of cooling fans that are either beginning to fail or dirt clogging up the system which causes the CPU to run a lot hotter. You'd be amazed at the kind of dirt that finds itself on those cooling fans and heat sinks, especially if the system is near or on the carpet, people are smoking around the system, and so on. The symptoms/failures would be varied between Windows and Ubuntu for the simple reason that each of them uses CPU and memory resources differently.

I've built, repaired, and upgraded literally hundreds of computers, probably at least 300 of them, and have never seen a disk drive that failed with less than 4 years of constant use ... unless something physical happened to damage the disk (falling to the ground, PC getting hit by a flying football, no kidding,). I've worked on power user and server machines that run constantly, 24 X 7 without ever being powered down, and hard disks never failed. People are freaking out way more than needed about hard disk issues while not looking at more appropriate areas of concern.

Proper cooling and cleanliness are the keys to a smoothly running computer. That's why big companies keep their servers in air conditioned enclosures. A lot of laptops can get pretty clogged up with dirt and dust too, especially if it spends a lot of time on the couch, your lap, the bed, and so on. Check your cooling fans and heat sink before you do anything else. Get a small paintbrush to clean all of the crud out. That's very easy to do. How old is this computer? Is it a laptop or a desktop PC unit? Which version of Ubuntu are you running on this system? Failing memory could cause problems like this too, but it's pretty unlikely.

**BTW:**  I always receive error messages with testdisk and other MBR utilities but as long as your disk health checks out with the disk utility, I really wouldn't worry about it at all. Matter of fact, just recently I had to do some data recovery from two different disks, one of them a refurbished 3+ year old generic ATA drive. Both disks are perfectly fine and disk health checks out 100% okay, even though testdisk still shows errors.

That was my first guess,  i alwasys keep my comuter clean (since i am changing it a lot.
The system temperature is not a problem too i have water cooling.
I have a always a temperature meter in my AwesomeWM desktop.

My hint is probably the motherboard or the hard disk.

Thanks anyway.

---

### Post by masterkorp on 2010-12-11
> **HankB said:**
> That seems like it would indicate what the problem is. Unfortunately I don't know what the various codes mean.

I would send a copy of that to Samsung to see if they can identify the problem.

Another thing to do is to make sure cables are firmly attached and so on. I would be thinking about replacing the disk at this point but I cannot rule out a cabling or power supply issue.

You might also look for a computer hardware oriented forum where you might find someone who can interpret those codes or will recognize the problem. It might also be worth googling the drive ID to see if it is a common problem with that model (like the problems common with the Deathstars.)

thanks, i will give notices about this.

---

