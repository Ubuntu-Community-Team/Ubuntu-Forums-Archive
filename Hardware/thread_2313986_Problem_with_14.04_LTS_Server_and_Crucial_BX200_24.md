---
title: "Problem with 14.04 LTS Server and Crucial BX200 240GB SSD"
date: 2016-02-17
forum: Hardware
---

### Post by jzambon on 2016-02-17
I purchased a Crucial BX200 SSD to replace a failed spinning drive.  I backed up my files from my 14.04 LTS Server (was temporarily running on a 64GB USB flash disk), ran dd to mirror all of the data from the USB disk over to the new SSD, expanded the partition, restarted and everything worked... for about a day.

After about a day of uptime, of 2 things will happen, 1) It will either freeze with no output to the screen.  REISUB/O cannot shut it down, and I have to power off with the reset button (yuck).  2) It will appear to be working, I will try to login and am presented with the following and get kicked out immediately...

```

XXXX@X.X.X.X's password: 
Failed to add entry for user XXXX.


Welcome to Ubuntu 14.04.3 LTS (GNU/Linux 3.19.0-25-generic x86_64)


 * Documentation:  https://help.ubuntu.com/


  System information as of Tue Feb 16 13:23:30 EST 2016


  System load: 0.08               Memory usage: 1%   Processes:       97
  Usage of /:  2.8% of 215.02GB   Swap usage:   0%   Users logged in: 0


  Graph this data and manage this system at:
    https://landscape.canonical.com/


35 packages can be updated.
13 updates are security updates.


sh: 1: /usr/bin/xauth: Input/output error
-bash: /etc/profile: Input/output error
-bash: /home/jbzambon/.profile: Input/output error
Connection to X.X.X.X closed.

```

Now, I assumed that flashing the new drive with dd and partitioning might have caused a problem with the install.  So I did a complete reinstall and restored important files (databases, etc.) from my still-working USB to the fresh 14.04 LTS install.  The problem persisted.

It will run stably for about 1 day, and then crash or dump me out with that Input/Output error.  I have yet to get more than 2 days of consecutive uptime with the new drive, whereas before I was getting months at a time without issue.

Additional troubleshooting with no success
1) Swapped in a known-working SATA cable
2) Swapped to a known-working SATA port
3) Swapped to a different SATA power port from the power supply (didn't swap power supplies)
3) RMAd the drive with Amazon and received a new drive in a couple days.  Ran dd to copy data from the original drive to its identical twin.
4) Checked compatibility with my motherboard (ASUS P5N-E), [Crucial has it listed as compatible]("http://www.crucial.com/usa/en/p5n-e-sli/CT7450064")

One time after running for a while, I rebooted and the drive wouldn't even pop into the BIOS.  Given that there is a time-limit to this, could it be possible that the drive is overheating?  I have 3 3TB drives in a RAID-5 alongside that are performing fine.

I'm reaching at this point as I cannot figure out why this is happening, any advice or additional troubleshooting steps would be much appreciated!

---

### Post by weatherman2 on 2016-02-17
I was poking around on Crucial's website.  They have a fairly new (1/12/16 - version MU02) firmware update available for the BX200 - have you tried to install it?  Unfortunately, you might need Windows for that.

Check the S.M.A.R.T. status of the drive.  Your version of GSmartControl might not have the correct S.M.A.R.T. attribute labels for it, but you can look them up (to see what the numbered attributes really mean).  This seems to correspond to their latest firmware:

[https://www.smartmontools.org/ticket/643](https://www.smartmontools.org/ticket/643)

My Crucial M500 SSD (running for almost two years in my netbook with Ubuntu 12.04 - never crashes) reports temperature as S.M.A.R.T attribute #194 (GSmartControl has the correct label for mine).  It does not get hot - currently idling at about 26C when in use.

I'd also look at your /var/log/syslog file for clues.

---

### Post by jzambon on 2016-02-17
Thanks for the hint on checking /var/log/syslog.  I did and noticed a lot of hte issues occurred after the system ran its daily cron jobs.  So, I figured that the problem had to do with the daily crontab.

I went in and ran each process individually.  When it was running /etc/cron.daily/mlocate, all hell broke loose and I was able to reproduce this seemingly "random" issue...

```

[28327.116037] ata4: EH in SWNCQ mode,QC:qc_active 0x7FFFFFFF sactive 0x7FFFFFFF
[28327.116081] ata4: SWNCQ:qc_active 0x18000000 defer_bits 0x67FFFFFF last_issue_tag 0x1c
[28327.116081]   dhfis 0x8000000 dmafis 0x0 sdbfis 0x4000000
[28327.116143] ata4: ATA_REG 0x41 ERR_REG 0x84
[28327.116163] ata4: tag : dhfis dmafis sdbfis sactive
[28327.116187] ata4: tag 0x1b: 1 0 0 1  
[28327.116205] ata4: tag 0x1c: 0 0 0 1  
[28327.116231] ata4.00: exception Emask 0x1 SAct 0x7fffffff SErr 0x0 action 0x6 frozen
[28327.116267] ata4.00: Ata error. fis:0x21
[28327.116288] ata4.00: failed command: READ FPDMA QUEUED
[28327.116316] ata4.00: cmd 60/08:00:30:09:c0/00:00:10:00:00/40 tag 0 ncq 4096 in
[28327.116316]          res 41/84:e0:18:09:c0/84:00:10:00:00/40 Emask 0x10 (ATA bus error)
[28327.116383] ata4.00: status: { DRDY ERR }
[28327.116403] ata4.00: error: { ICRC ABRT }
[28327.116423] ata4.00: failed command: READ FPDMA QUEUED
[28327.116450] ata4.00: cmd 60/08:08:38:09:c0/00:00:10:00:00/40 tag 1 ncq 4096 in
[28327.116450]          res 41/84:e0:18:09:c0/84:00:10:00:00/40 Emask 0x10 (ATA bus error)
[28327.116517] ata4.00: status: { DRDY ERR }
[28327.116537] ata4.00: error: { ICRC ABRT }
[28327.116557] ata4.00: failed command: READ FPDMA QUEUED
[28327.116584] ata4.00: cmd 60/08:10:40:09:c0/00:00:10:00:00/40 tag 2 ncq 4096 in
[28327.116584]          res 41/84:e0:18:09:c0/84:00:10:00:00/40 Emask 0x10 (ATA bus error)
[28327.116651] ata4.00: status: { DRDY ERR }
[28327.116671] ata4.00: error: { ICRC ABRT }
[28327.116690] ata4.00: failed command: READ FPDMA QUEUED
[28327.116718] ata4.00: cmd 60/08:18:50:09:c0/00:00:10:00:00/40 tag 3 ncq 4096 in
[28327.116718]          res 41/84:e0:18:09:c0/84:00:10:00:00/40 Emask 0x10 (ATA bus error)
[28327.116784] ata4.00: status: { DRDY ERR }
[28327.116804] ata4.00: error: { ICRC ABRT }
[28327.116824] ata4.00: failed command: READ FPDMA QUEUED
[28327.116851] ata4.00: cmd 60/08:20:58:09:c0/00:00:10:00:00/40 tag 4 ncq 4096 in
[28327.116851]          res 41/84:e0:18:09:c0/84:00:10:00:00/40 Emask 0x10 (ATA bus error)
[28327.116918] ata4.00: status: { DRDY ERR }
[28327.116938] ata4.00: error: { ICRC ABRT }
[28327.116958] ata4.00: failed command: READ FPDMA QUEUED
[28327.116985] ata4.00: cmd 60/08:28:60:09:c0/00:00:10:00:00/40 tag 5 ncq 4096 in
[28327.116985]          res 41/84:e0:18:09:c0/84:00:10:00:00/40 Emask 0x10 (ATA bus error)
[28327.117052] ata4.00: status: { DRDY ERR }
[28327.117072] ata4.00: error: { ICRC ABRT }
[28327.117092] ata4.00: failed command: READ FPDMA QUEUED
[28327.117119] ata4.00: cmd 60/08:30:68:09:c0/00:00:10:00:00/40 tag 6 ncq 4096 in
[28327.117119]          res 41/84:e0:18:09:c0/84:00:10:00:00/40 Emask 0x10 (ATA bus error)
[28327.117186] ata4.00: status: { DRDY ERR }
[28327.117206] ata4.00: error: { ICRC ABRT }
[28327.117225] ata4.00: failed command: READ FPDMA QUEUED
[28327.117253] ata4.00: cmd 60/08:38:70:09:c0/00:00:10:00:00/40 tag 7 ncq 4096 in
[28327.117253]          res 41/84:e0:18:09:c0/84:00:10:00:00/40 Emask 0x10 (ATA bus error)
[28327.117320] ata4.00: status: { DRDY ERR }
[28327.117340] ata4.00: error: { ICRC ABRT }
[28327.117360] ata4.00: failed command: READ FPDMA QUEUED
[28327.117387] ata4.00: cmd 60/08:40:78:09:c0/00:00:10:00:00/40 tag 8 ncq 4096 in
[28327.117387]          res 41/84:e0:18:09:c0/84:00:10:00:00/40 Emask 0x10 (ATA bus error)
[28327.117454] ata4.00: status: { DRDY ERR }
[28327.117474] ata4.00: error: { ICRC ABRT }
[28327.117494] ata4.00: failed command: READ FPDMA QUEUED
[28327.117521] ata4.00: cmd 60/08:48:80:09:c0/00:00:10:00:00/40 tag 9 ncq 4096 in
[28327.117521]          res 41/84:e0:18:09:c0/84:00:10:00:00/40 Emask 0x10 (ATA bus error)
[28327.117588] ata4.00: status: { DRDY ERR }
[28327.117607] ata4.00: error: { ICRC ABRT }
[28327.117627] ata4.00: failed command: READ FPDMA QUEUED
[28327.117655] ata4.00: cmd 60/08:50:88:09:c0/00:00:10:00:00/40 tag 10 ncq 4096 in
[28327.117655]          res 41/84:e0:18:09:c0/84:00:10:00:00/40 Emask 0x10 (ATA bus error)
[28327.120471] ata4.00: status: { DRDY ERR }
[28327.121902] ata4.00: error: { ICRC ABRT }
[28327.123282] ata4.00: failed command: READ FPDMA QUEUED
[28327.124662] ata4.00: cmd 60/08:58:90:09:c0/00:00:10:00:00/40 tag 11 ncq 4096 in
[28327.124662]          res 41/84:e0:18:09:c0/84:00:10:00:00/40 Emask 0x10 (ATA bus error)
[28327.127403] ata4.00: status: { DRDY ERR }
[28327.128784] ata4.00: error: { ICRC ABRT }
[28327.130159] ata4.00: failed command: READ FPDMA QUEUED
[28327.131549] ata4.00: cmd 60/08:60:98:09:c0/00:00:10:00:00/40 tag 12 ncq 4096 in
[28327.131549]          res 41/84:e0:18:09:c0/84:00:10:00:00/40 Emask 0x10 (ATA bus error)
[28327.134349] ata4.00: status: { DRDY ERR }
[28327.135741] ata4.00: error: { ICRC ABRT }
[28327.137123] ata4.00: failed command: READ FPDMA QUEUED
[28327.138505] ata4.00: cmd 60/08:68:a0:09:c0/00:00:10:00:00/40 tag 13 ncq 4096 in
[28327.138505]          res 41/84:e0:18:09:c0/84:00:10:00:00/40 Emask 0x10 (ATA bus error)
[28327.141288] ata4.00: status: { DRDY ERR }
[28327.142684] ata4.00: error: { ICRC ABRT }
[28327.144073] ata4.00: failed command: READ FPDMA QUEUED
[28327.145460] ata4.00: cmd 60/08:70:a8:09:c0/00:00:10:00:00/40 tag 14 ncq 4096 in
[28327.145460]          res 41/84:e0:18:09:c0/84:00:10:00:00/40 Emask 0x10 (ATA bus error)
[28327.148246] ata4.00: status: { DRDY ERR }
[28327.149650] ata4.00: error: { ICRC ABRT }
[28327.151038] ata4.00: failed command: READ FPDMA QUEUED
[28327.152431] ata4.00: cmd 60/08:78:b0:09:c0/00:00:10:00:00/40 tag 15 ncq 4096 in
[28327.152431]          res 41/84:e0:18:09:c0/84:00:10:00:00/40 Emask 0x10 (ATA bus error)
[28327.155227] ata4.00: status: { DRDY ERR }
[28327.156638] ata4.00: error: { ICRC ABRT }
[28327.158033] ata4.00: failed command: READ FPDMA QUEUED
[28327.159424] ata4.00: cmd 60/08:80:b8:09:c0/00:00:10:00:00/40 tag 16 ncq 4096 in
[28327.159424]          res 41/84:e0:18:09:c0/84:00:10:00:00/40 Emask 0x10 (ATA bus error)
[28327.162231] ata4.00: status: { DRDY ERR }
[28327.163644] ata4.00: error: { ICRC ABRT }
[28327.165043] ata4.00: failed command: READ FPDMA QUEUED
[28327.166446] ata4.00: cmd 60/08:88:c0:09:c0/00:00:10:00:00/40 tag 17 ncq 4096 in
[28327.166446]          res 41/84:e0:18:09:c0/84:00:10:00:00/40 Emask 0x10 (ATA bus error)
[28327.169266] ata4.00: status: { DRDY ERR }
[28327.170684] ata4.00: error: { ICRC ABRT }
[28327.172089] ata4.00: failed command: READ FPDMA QUEUED
[28327.173496] ata4.00: cmd 60/08:90:c8:09:c0/00:00:10:00:00/40 tag 18 ncq 4096 in
[28327.173496]          res 41/84:e0:18:09:c0/84:00:10:00:00/40 Emask 0x10 (ATA bus error)
[28327.176321] ata4.00: status: { DRDY ERR }
[28327.177740] ata4.00: error: { ICRC ABRT }
[28327.179145] ata4.00: failed command: READ FPDMA QUEUED
[28327.180559] ata4.00: cmd 60/08:98:d0:09:c0/00:00:10:00:00/40 tag 19 ncq 4096 in
[28327.180559]          res 41/84:e0:18:09:c0/84:00:10:00:00/40 Emask 0x10 (ATA bus error)
[28327.183393] ata4.00: status: { DRDY ERR }
[28327.184826] ata4.00: error: { ICRC ABRT }
[28327.186239] ata4.00: failed command: READ FPDMA QUEUED
[28327.187653] ata4.00: cmd 60/08:a0:d8:09:c0/00:00:10:00:00/40 tag 20 ncq 4096 in
[28327.187653]          res 41/84:e0:18:09:c0/84:00:10:00:00/40 Emask 0x10 (ATA bus error)
[28327.190495] ata4.00: status: { DRDY ERR }
[28327.191931] ata4.00: error: { ICRC ABRT }
[28327.193353] ata4.00: failed command: READ FPDMA QUEUED
[28327.194775] ata4.00: cmd 60/08:a8:e0:09:c0/00:00:10:00:00/40 tag 21 ncq 4096 in
[28327.194775]          res 41/84:e0:18:09:c0/84:00:10:00:00/40 Emask 0x10 (ATA bus error)
[28327.197631] ata4.00: status: { DRDY ERR }
[28327.199066] ata4.00: error: { ICRC ABRT }
[28327.200492] ata4.00: failed command: READ FPDMA QUEUED
[28327.201918] ata4.00: cmd 60/08:b0:e8:09:c0/00:00:10:00:00/40 tag 22 ncq 4096 in
[28327.201918]          res 41/84:e0:18:09:c0/84:00:10:00:00/40 Emask 0x10 (ATA bus error)
[28327.204782] ata4.00: status: { DRDY ERR }
[28327.206221] ata4.00: error: { ICRC ABRT }
[28327.207646] ata4.00: failed command: READ FPDMA QUEUED
[28327.209079] ata4.00: cmd 60/08:b8:f0:09:c0/00:00:10:00:00/40 tag 23 ncq 4096 in
[28327.209079]          res 41/84:e0:18:09:c0/84:00:10:00:00/40 Emask 0x10 (ATA bus error)
[28327.211947] ata4.00: status: { DRDY ERR }
[28327.213395] ata4.00: error: { ICRC ABRT }
[28327.214827] ata4.00: failed command: READ FPDMA QUEUED
[28327.216267] ata4.00: cmd 60/08:c0:f8:09:c0/00:00:10:00:00/40 tag 24 ncq 4096 in
[28327.216267]          res 41/84:e0:18:09:c0/84:00:10:00:00/40 Emask 0x10 (ATA bus error)
[28327.219137] ata4.00: status: { DRDY ERR }
[28327.220582] ata4.00: error: { ICRC ABRT }
[28327.222006] ata4.00: failed command: READ FPDMA QUEUED
[28327.223434] ata4.00: cmd 60/08:c8:00:0a:c0/00:00:10:00:00/40 tag 25 ncq 4096 in
[28327.223434]          res 41/84:e0:18:09:c0/84:00:10:00:00/40 Emask 0x10 (ATA bus error)
[28327.226313] ata4.00: status: { DRDY ERR }
[28327.227761] ata4.00: error: { ICRC ABRT }
[28327.229195] ata4.00: failed command: READ FPDMA QUEUED
[28327.230626] ata4.00: cmd 60/08:d0:48:09:c0/00:00:10:00:00/40 tag 26 ncq 4096 in
[28327.230626]          res 41/84:e0:18:09:c0/84:00:10:00:00/40 Emask 0x10 (ATA bus error)
[28327.233501] ata4.00: status: { DRDY ERR }
[28327.234945] ata4.00: error: { ICRC ABRT }
[28327.236378] ata4.00: failed command: READ FPDMA QUEUED
[28327.237811] ata4.00: cmd 60/08:d8:10:09:c0/00:00:10:00:00/40 tag 27 ncq 4096 in
[28327.237811]          res 41/84:e0:18:09:c0/84:00:10:00:00/40 Emask 0x10 (ATA bus error)
[28327.240681] ata4.00: status: { DRDY ERR }
[28327.242122] ata4.00: error: { ICRC ABRT }
[28327.243546] ata4.00: failed command: READ FPDMA QUEUED
[28327.244976] ata4.00: cmd 60/08:e0:18:09:c0/00:00:10:00:00/40 tag 28 ncq 4096 in
[28327.244976]          res 41/84:e0:18:09:c0/84:00:10:00:00/40 Emask 0x10 (ATA bus error)
[28327.247838] ata4.00: status: { DRDY ERR }
[28327.249280] ata4.00: error: { ICRC ABRT }
[28327.250706] ata4.00: failed command: READ FPDMA QUEUED
[28327.252135] ata4.00: cmd 60/08:e8:20:09:c0/00:00:10:00:00/40 tag 29 ncq 4096 in
[28327.252135]          res 41/84:e0:18:09:c0/84:00:10:00:00/40 Emask 0x10 (ATA bus error)
[28327.254999] ata4.00: status: { DRDY ERR }
[28327.256441] ata4.00: error: { ICRC ABRT }
[28327.257866] ata4.00: failed command: READ FPDMA QUEUED
[28327.259290] ata4.00: cmd 60/08:f0:28:09:c0/00:00:10:00:00/40 tag 30 ncq 4096 in
[28327.259290]          res 41/84:e0:18:09:c0/84:00:10:00:00/40 Emask 0x10 (ATA bus error)
[28327.262155] ata4.00: status: { DRDY ERR }
[28327.263596] ata4.00: error: { ICRC ABRT }
[28327.265027] ata4: hard resetting link
[28327.265030] ata4: nv: skipping hardreset on occupied port
[28327.732026] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[28327.748049] ata4.00: both IDENTIFYs aborted, assuming NODEV
[28327.748052] ata4.00: revalidation failed (errno=-2)
[28332.732019] ata4: hard resetting link
[28332.732023] ata4: nv: skipping hardreset on occupied port
[28333.200025] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[28333.216045] ata4.00: both IDENTIFYs aborted, assuming NODEV
[28333.216048] ata4.00: revalidation failed (errno=-2)
[28338.200018] ata4: hard resetting link
[28338.200022] ata4: nv: skipping hardreset on occupied port
[28338.668028] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[28338.684045] ata4.00: both IDENTIFYs aborted, assuming NODEV
[28338.684047] ata4.00: revalidation failed (errno=-2)
[28338.685444] ata4.00: disabled
[28338.685476] sd 3:0:0:0: [sda] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[28338.685480] sd 3:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[28338.685484] sd 3:0:0:0: [sda] Add. Sense: Scsi parity error
[28338.685487] sd 3:0:0:0: [sda] CDB: 
[28338.685489] Read(10): 28 00 10 c0 09 30 00 00 08 00
[28338.685498] blk_update_request: I/O error, dev sda, sector 281020720
[28338.686911] sd 3:0:0:0: [sda] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[28338.686914] sd 3:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[28338.686917] sd 3:0:0:0: [sda] Add. Sense: Scsi parity error
[28338.686919] sd 3:0:0:0: [sda] CDB: 
[28338.686921] Read(10): 28 00 10 c0 09 38 00 00 08 00
[28338.686928] blk_update_request: I/O error, dev sda, sector 281020728
[28338.688322] sd 3:0:0:0: [sda] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[28338.688331] sd 3:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[28338.688339] sd 3:0:0:0: [sda] Add. Sense: Scsi parity error
[28338.688341] sd 3:0:0:0: [sda] CDB: 
[28338.688343] Read(10): 28 00 10 c0 09 40 00 00 08 00
[28338.688350] blk_update_request: I/O error, dev sda, sector 281020736
[28338.689715] sd 3:0:0:0: [sda] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[28338.689718] sd 3:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[28338.689721] sd 3:0:0:0: [sda] Add. Sense: Scsi parity error
[28338.689723] sd 3:0:0:0: [sda] CDB: 
[28338.689724] Read(10): 28 00 10 c0 09 50 00 00 08 00
[28338.689732] blk_update_request: I/O error, dev sda, sector 281020752
[28338.691067] sd 3:0:0:0: [sda] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[28338.691070] sd 3:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[28338.691073] sd 3:0:0:0: [sda] Add. Sense: Scsi parity error
[28338.691075] sd 3:0:0:0: [sda] CDB: 
[28338.691077] Read(10): 28 00 10 c0 09 58 00 00 08 00
[28338.691084] blk_update_request: I/O error, dev sda, sector 281020760
[28338.692427] sd 3:0:0:0: [sda] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[28338.692435] sd 3:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[28338.692443] sd 3:0:0:0: [sda] Add. Sense: Scsi parity error
[28338.692446] sd 3:0:0:0: [sda] CDB: 
[28338.692447] Read(10): 28 00 10 c0 09 60 00 00 08 00
[28338.692454] blk_update_request: I/O error, dev sda, sector 281020768
[28338.693774] sd 3:0:0:0: [sda] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[28338.693777] sd 3:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[28338.693780] sd 3:0:0:0: [sda] Add. Sense: Scsi parity error
[28338.693782] sd 3:0:0:0: [sda] CDB: 
[28338.693783] Read(10): 28 00 10 c0 09 68 00 00 08 00
[28338.693791] blk_update_request: I/O error, dev sda, sector 281020776
[28338.695092] sd 3:0:0:0: [sda] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[28338.695095] sd 3:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[28338.695098] sd 3:0:0:0: [sda] Add. Sense: Scsi parity error
[28338.695101] sd 3:0:0:0: [sda] CDB: 
[28338.695102] Read(10): 28 00 10 c0 09 70 00 00 08 00
[28338.695109] blk_update_request: I/O error, dev sda, sector 281020784
[28338.696398] sd 3:0:0:0: [sda] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[28338.696406] sd 3:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[28338.696414] sd 3:0:0:0: [sda] Add. Sense: Scsi parity error
[28338.696417] sd 3:0:0:0: [sda] CDB: 
[28338.696418] Read(10): 28 00 10 c0 09 78 00 00 08 00
[28338.696425] blk_update_request: I/O error, dev sda, sector 281020792
[28338.697684] sd 3:0:0:0: [sda] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[28338.697687] sd 3:0:0:0: [sda] Sense Key : Aborted Command [current] [descriptor]
[28338.697690] sd 3:0:0:0: [sda] Add. Sense: Scsi parity error
[28338.697693] sd 3:0:0:0: [sda] CDB: 
[28338.697694] Read(10): 28 00 10 c0 09 80 00 00 08 00
[28338.697701] blk_update_request: I/O error, dev sda, sector 281020800
[28338.698990] ata4: EH complete
[28338.699027] EXT4-fs error (device sda1): __ext4_get_inode_loc:3771: inode #8781983: block 35127337: comm updatedb.mlocat: unable to read itable block
[28338.699040] EXT4-fs warning (device sda1): ext4_end_bio:317: I/O error -5 writing to inode 1050656 (offset 0 size 4096 starting block 30446476)
[28338.699043] Buffer I/O error on device sda1, logical block 30446219
[28338.699051] EXT4-fs warning (device sda1): ext4_end_bio:317: I/O error -5 writing to inode 1050656 (offset 8192 size 4096 starting block 30446477)
[28338.699053] Buffer I/O error on device sda1, logical block 30446220
[28338.699372] EXT4-fs warning (device sda1): ext4_end_bio:317: I/O error -5 writing to inode 3413879 (offset 6885376 size 4096 starting block 38019986)
[28338.699373] Buffer I/O error on device sda1, logical block 38019729
[28338.699378] EXT4-fs warning (device sda1): ext4_end_bio:317: I/O error -5 writing to inode 3413879 (offset 0 size 0 starting block 38019985)
[28338.699380] Buffer I/O error on device sda1, logical block 38019728
[28338.699669] Aborting journal on device sda1-8.
[28338.699709] Buffer I/O error on dev sda1, logical block 28344320, lost sync page write
[28338.699715] JBD2: Error -5 detected when updating journal superblock for sda1-8.
[28338.704768] Buffer I/O error on dev sda1, logical block 0, lost sync page write
[28338.704779] EXT4-fs error (device sda1): ext4_journal_check_start:56: Detected aborted journal
[28338.704781] EXT4-fs (sda1): Remounting filesystem read-only
[28338.704783] EXT4-fs (sda1): previous I/O error to superblock detected
[28338.704794] Buffer I/O error on dev sda1, logical block 0, lost sync page write
[28338.717028] EXT4-fs (sda1): previous I/O error to superblock detected
[28338.718509] Buffer I/O error on dev sda1, logical block 0, lost sync page write
[28338.720296] EXT4-fs error (device sda1): ext4_find_entry:1289: inode #5637865: comm updatedb.mlocat: reading directory lblock 0
[28338.721770] EXT4-fs (sda1): previous I/O error to superblock detected
[28338.723238] Buffer I/O error on dev sda1, logical block 0, lost sync page write
[28338.724935] EXT4-fs error (device sda1): ext4_find_entry:1289: inode #5637865: comm updatedb.mlocat: reading directory lblock 0
[28338.726429] EXT4-fs (sda1): previous I/O error to superblock detected
[28338.727931] Buffer I/O error on dev sda1, logical block 0, lost sync page write
[28338.729726] EXT4-fs error (device sda1): ext4_find_entry:1289: inode #5637865: comm updatedb.mlocat: reading directory lblock 0
[28338.731281] EXT4-fs (sda1): previous I/O error to superblock detected
[28338.732967] Buffer I/O error on dev sda1, logical block 0, lost sync page write
[28338.734568] EXT4-fs error (device sda1): ext4_find_entry:1289: inode #5637865: comm updatedb.mlocat: reading directory lblock 0
[28338.736208] EXT4-fs (sda1): previous I/O error to superblock detected
[28338.738007] Buffer I/O error on dev sda1, logical block 0, lost sync page write
[28338.739647] EXT4-fs error (device sda1): ext4_find_entry:1289: inode #5637865: comm updatedb.mlocat: reading directory lblock 0
[28338.741350] EXT4-fs (sda1): previous I/O error to superblock detected
[28338.743057] Buffer I/O error on dev sda1, logical block 0, lost sync page write
[28338.745005] EXT4-fs error (device sda1): ext4_find_entry:1289: inode #7995999: comm updatedb.mlocat: reading directory lblock 0
[28338.746727] EXT4-fs (sda1): previous I/O error to superblock detected
[28338.748489] Buffer I/O error on dev sda1, logical block 0, lost sync page write
[28338.750344] EXT4-fs error (device sda1): ext4_find_entry:1289: inode #5506636: comm updatedb.mlocat: reading directory lblock 0
[28338.752122] EXT4-fs (sda1): previous I/O error to superblock detected
[28338.753971] EXT4-fs error (device sda1): ext4_find_entry:1289: inode #8258894: comm updatedb.mlocat: reading directory lblock 0
[28338.755963] EXT4-fs error (device sda1): ext4_find_entry:1289: inode #8258894: comm updatedb.mlocat: reading directory lblock 0
[28338.758685] EXT4-fs warning (device sda1): __ext4_read_dirblock:884: error -5 reading directory block (ino 6687018, block 0)
[28338.758724] EXT4-fs warning (device sda1): __ext4_read_dirblock:884: error -5 reading directory block (ino 5506625, block 0)
[28338.758758] EXT4-fs warning (device sda1): __ext4_read_dirblock:884: error -5 reading directory block (ino 4589062, block 0)
[28338.758795] EXT4-fs warning (device sda1): __ext4_read_dirblock:884: error -5 reading directory block (ino 5113404, block 0)
[28338.758829] EXT4-fs warning (device sda1): __ext4_read_dirblock:884: error -5 reading directory block (ino 6429113, block 0)
[28338.758862] EXT4-fs warning (device sda1): __ext4_read_dirblock:884: error -5 reading directory block (ino 5244596, block 0)

```

These errors repeated and I was unable to turn off the machine except to physically hit the reset button.  Upon restart, the system behaved normally.  I re-ran all of the daily cron jobs and it completed successfully, so it still appears to be somewhat random.  I'm left with the following thoughts...

1) The drive is defective (making me 0/2 on getting a working drive)
2) My motherboard is starting to die
3) Manually running mlocate magically fixed my issue and I never have to worry about anything ever again!

I'm checking the drive with a smart long test right now and will report back any results.  Thanks again for the tip on /var/log/syslog.1-8!

---

### Post by jzambon on 2016-02-17
Update, smartctl test finished quickly, and not well...

```

jbzambon@bigsherman:~$ sudo smartctl -a /dev/sda
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.19.0-25-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Device Model:     CT240BX200SSD1
Serial Number:    1548F011A55F
LU WWN Device Id: 5 00a075 1f011a55f
Firmware Version: MU01.4
User Capacity:    240,057,409,536 bytes [240 GB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    Solid State Device
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ACS-2 (minor revision not indicated)
SATA Version is:  SATA 3.1, 6.0 Gb/s (current: 1.5 Gb/s)
Local Time is:    Wed Feb 17 22:11:48 2016 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x80)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      ( 241)	Self-test routine in progress...
					10% of test remaining.
Total time to complete Offline 
data collection: 		(  120) seconds.
Offline data collection
capabilities: 			 (0x71) SMART execute Offline immediate.
					No Auto Offline data collection support.
					Suspend Offline collection upon new
					command.
					No Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0002)	Does not save SMART data before
					entering power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 (   2) minutes.
Conveyance self-test routine
recommended polling time: 	 (   1) minutes.
SCT capabilities: 	       (0x0035)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.


SMART Attributes Data Structure revision number: 1
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x0000   100   100   000    Old_age   Offline      -       0
  5 Reallocated_Sector_Ct   0x0000   100   100   000    Old_age   Offline      -       0
  9 Power_On_Hours          0x0000   100   100   000    Old_age   Offline      -       7
 12 Power_Cycle_Count       0x0000   100   100   000    Old_age   Offline      -       9
160 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       0
161 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       30
163 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       307
148 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       4399
149 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       84
150 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       0
151 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       62
164 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       1470
165 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       5
166 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       1
167 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       1
169 Unknown_Attribute       0x0000   100   100   001    Old_age   Offline      -       100
181 Program_Fail_Cnt_Total  0x0000   100   100   000    Old_age   Offline      -       0
182 Erase_Fail_Count_Total  0x0000   100   100   000    Old_age   Offline      -       0
192 Power-Off_Retract_Count 0x0000   100   100   000    Old_age   Offline      -       2
194 Temperature_Celsius     0x0000   100   100   070    Old_age   Offline      -       26 (33 34 38 34 0)
199 UDMA_CRC_Error_Count    0x0000   100   100   000    Old_age   Offline      -       8
232 Available_Reservd_Space 0x0000   100   100   000    Old_age   Offline      -       100
241 Total_LBAs_Written      0x0000   100   100   000    Old_age   Offline      -       8165
242 Total_LBAs_Read         0x0000   100   100   000    Old_age   Offline      -       7337
245 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       8682
246 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       8798
247 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       0


Read SMART Error Log failed: scsi error aborted command


Read SMART Self-test Log failed: scsi error aborted command


Read SMART Selective Self-test Log failed: scsi error aborted command

```

Is there something I'm missing is this another bad drive or bad mobo?

My next thing will be to update the drive firmware as suggested.  Thanks!

---

### Post by weatherman2 on 2016-02-17
> Firmware Version: MU01.4

Yes, I would find a way to install the newest firmware before trying anything else.  If there is some firmware issue that causes Linux problems, it would have existed in both drives you have tried so far.

---

### Post by jzambon on 2016-02-18
Okay, after about 6 hours of figuring it out from a Mac, I was able to get the firmware update CD burned and firmware updated.  Pro-tip for all mac users: don't bother with a USB disk and just find someone with an external CD burner.  I spent about 3 hours playing around with Windows 8 through Virtual Box on my laptop and a spare SATA -> USB converter.  Then I spent about 3 hours trying to make a bootable USB key.  Finally, I gave up and borrowed a CD burner and burned the firmware update ISO to a blank CD-R, which took all of 3 minutes.  Ugh...

So now my drive is updated but still refuses to do the long test with these errors (full output of smartctl below).

```

Read SMART Error Log failed: scsi error aborted command


Read SMART Self-test Log failed: scsi error aborted command


Read SMART Selective Self-test Log failed: scsi error aborted command

```

I don't know if my drive will crash again, but I ran all of the cron.daily tasks with no problems.  I will cross my fingers and hope for the best.


```

XXX@XXX:~$ sudo smartctl -a /dev/sda
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.19.0-25-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Device Model:     CT240BX200SSD1
Serial Number:    1548F011A55F
LU WWN Device Id: 5 00a075 1f011a55f
**Firmware Version: MU02.6**
User Capacity:    240,057,409,536 bytes [240 GB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    Solid State Device
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ACS-2 (minor revision not indicated)
SATA Version is:  SATA 3.1, 6.0 Gb/s (current: 1.5 Gb/s)
Local Time is:    Thu Feb 18 13:42:40 2016 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x02)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		(  171) seconds.
Offline data collection
capabilities: 			 (0x71) SMART execute Offline immediate.
					No Auto Offline data collection support.
					Suspend Offline collection upon new
					command.
					No Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0002)	Does not save SMART data before
					entering power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 (   2) minutes.
Conveyance self-test routine
recommended polling time: 	 (   1) minutes.
SCT capabilities: 	       (0x0035)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.


SMART Attributes Data Structure revision number: 1
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x0000   100   100   000    Old_age   Offline      -       0
  5 Reallocated_Sector_Ct   0x0000   100   100   000    Old_age   Offline      -       0
  9 Power_On_Hours          0x0000   100   100   000    Old_age   Offline      -       7
 12 Power_Cycle_Count       0x0000   100   100   000    Old_age   Offline      -       37
160 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       0
161 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       30
163 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       307
148 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       4424
149 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       84
150 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       0
151 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       63
164 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       1474
165 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       6
166 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       1
167 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       1
169 Unknown_Attribute       0x0000   100   100   001    Old_age   Offline      -       100
181 Program_Fail_Cnt_Total  0x0000   100   100   000    Old_age   Offline      -       0
182 Erase_Fail_Count_Total  0x0000   100   100   000    Old_age   Offline      -       0
192 Power-Off_Retract_Count 0x0000   100   100   000    Old_age   Offline      -       3
194 Temperature_Celsius     0x0000   100   100   070    Old_age   Offline      -       25 (31 33 36 33 0)
199 UDMA_CRC_Error_Count    0x0000   100   100   000    Old_age   Offline      -       0
232 Available_Reservd_Space 0x0000   100   100   000    Old_age   Offline      -       100
241 Total_LBAs_Written      0x0000   100   100   000    Old_age   Offline      -       8172
242 Total_LBAs_Read         0x0000   100   100   000    Old_age   Offline      -       7356
245 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       8705
246 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       8848
247 Unknown_Attribute       0x0000   100   100   000    Old_age   Offline      -       0


Read SMART Error Log failed: scsi error aborted command


Read SMART Self-test Log failed: scsi error aborted command


Read SMART Selective Self-test Log failed: scsi error aborted command

```

---

### Post by weatherman2 on 2016-02-18
I wouldn't worry about the S.M.A.R.T. test not passing, personally, on an SSD.  Could simply be an incompatibility with your version of SmartMonTools.  If Crucial offers some sort of diagnostic boot disc, you might try that to confirm it's OK.  Although I still find the S.M.A.R.T. Attributes useful for an SSD, running tests seems less useful.  I'm generally worried about a spinning hard disk's health and like the ability to test to inspect its surface, etc.  Not such a big worry for an SSD.

Otherwise, let's hope the firmware update fixes your actual problem!

What a pain trying to burn a USB boot of the update!  I understand your pain.  I recently tried to make a USB boot for an old Macbook Pro and could not get it to boot no matter what I tried.  I have booted Ubuntu via USB on newer Macbooks but not this one.  I've mostly moved away from burning discs myself but sometimes that's your best choice.

---

### Post by jzambon on 2016-02-18
I've had luck making bootable USB disks with Ubuntu using [this]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx"), these only work on non-Macs, though.  To get the disk to boot on a Mac, check out [reFind]("http://www.howtogeek.com/187410/how-to-install-and-dual-boot-linux-on-a-mac/").  I wish they made this easier. :x

That said, thanks for your help, I have almost 2 hours of uptime and no problems despite trying to tax the heck out of the disk. Also scrubbing the disk that I got the first time around to send back to Amazon.

```

~$ uptime
 15:49:12 up  1:59,  1 user,  load average: 0.00, 0.01, 0.05

```

---

### Post by weatherman2 on 2016-02-18
On the newer Macs, you can boot the same EFI-compatible USB boot disk that you boot on a PC.  I tried it for the first time last year on someone's 2012-era Macbook and Ubuntu 14.04 booted effortlessly from the same USB stick I've booted on lots of PCs.  The Mac I was playing with recently was a few years older - had EFI too but obviously didn't like any of the USB boot disks I tried.

Good luck with the SSD!

---

### Post by jzambon on 2016-02-20
The firmware upgrade looks to be working, gonna tag this as solved.  Thanks again!

```

~$ uptime
 21:31:09 up 2 days,  7:41,  1 user,  load average: 0.09, 0.18, 0.41

```

---

