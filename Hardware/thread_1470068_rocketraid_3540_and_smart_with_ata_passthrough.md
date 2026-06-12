---
title: "rocketraid 3540 and smart with ata passthrough"
date: 2010-05-02
forum: Hardware
---

### Post by donbowman on 2010-05-02
[FONT=Courier New]I have a rocketraid 3540 controller (driver v1.6, 090910) under 10.4
I have configured the raid controller to be 'non-raid' mode (e.g. ATA passthrough).
This gives me discrete devices (e.g. /dev/sda, /dev/sdb).

Generally things work fine, i was able to use those devices into a ZFS array.

Some errors though. For example, 
hdparm -i /dev/sda gives an error "(HDIO_DRIVE_CMD(identify) failed: invalid exchange".

And, 
smartctl -i /dev/sda gives 'device does not support SMART'.

Now, i would like to use SMART. If i use hptraidconf command line tool, i can:

[/FONT][FONT=Courier New]HighPoint CLI>query devices 1/3
Mode Number:    WDC WD20EARS-00S8B1 
Serial Number:  WD-WCAVY2755231
Capacity(GB):   2000.40             TotalFree(GB):  0
Status:         SINGLE              Flag:           LEGACY
Read Ahead:     enabled             Write Cache:    enabled
TCQ:            --                  NCQ:            enabled

I see from the smartmontools man page that there is a '-d hpt' option. But i can't figure out how to use it. THe syntax is:

'smartctl -i -d hpt,1/3 /dev/???'. Its the '???' i can't figure out. If i try 'sda', i get 'Device Read Identify Failed (not an ATA/ATAPI device).
If i try /dev/sg6, i get the same

If i 'strace -e file' hptraidconf, i see it uses a device 'sg6' to communicate. Smart informs me that this is a 'HPT RCM DEVICE'.

I would really prefer not to try and 'rewrite smart via the hptraidconf iface + expect'. I would really like to get the temperature etc from my raid.

As a side note, the 'hdparm -i' breakage causes some trouble with udev: the /dev/disk/* links don't work properly for these pass-through.

Has anyone any suggestions on using this rocketraid 3540 with linux and having smart work?

# uname -a Linux nas 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux

HighPoint CLI>query controllers
ID                              Channel         Name
1                               16              RocketRAID 3540 Controller
-------------------------------------------------------------------------------
IOP Model                       IOP341 800MHz
SDRAM Size                      256M
Battery Installed               No
Firmware Version                v1.2.17.14
Serial Number                   0824M3B000268
Battery MotherBoard Status      Not installed
-------------------------------------------------------------------------------

HighPoint CLI>query devices
ID      Capacity    MaxFree     Flag    Status    ModelNumber
-------------------------------------------------------------------------------
1/3     2000.40     0           SINGLE  LEGACY    WDC WD20EARS-00S8B1
1/5     2000.40     0           SINGLE  LEGACY    WDC WD20EARS-00S8B1
1/8     2000.40     0           SINGLE  LEGACY    WDC WD20EARS-00S8B1
1/10    2000.40     0           SINGLE  LEGACY    WDC WD20EARS-00S8B1
1/13    2000.40     0           SINGLE  LEGACY    WDC WD20EARS-00S8B1
1/15    2000.40     0           SINGLE  LEGACY    WDC WD20EARS-00S8B1
-------------------------------------------------------------------------------
HighPoint CLI>query device 1/3
HighPoint CLI>query devices 1/3
Mode Number:    WDC WD20EARS-00S8B1 
Serial Number:  WD-WCAVY2755231
Capacity(GB):   2000.40             TotalFree(GB):  0
Status:         SINGLE              Flag:           LEGACY
Read Ahead:     enabled             Write Cache:    enabled
TCQ:            --                  NCQ:            enabled
-------------------------------------------------------------------------------
                                S.M.A.R.T Attributes
Status: S.M.A.R.T OK.
ID  Name                           Threshold  Value      Worst      Status
-------------------------------------------------------------------------------
1   Raw Read Error Rate            51         200        200        OK
3   Spin Up Time                   21         182        174        OK
4   Start Stop Count               0          100        100        OK
5   Reallocated Sector Ct          140        200        200        OK
7   Seek Error Rate                0          200        200        OK
9   Power On Hours                 0          100        100        OK
A   Spin Retry Count               0          100        253        OK
B   Calibration Retry Count        0          100        253        OK
C   Power Cycle Count              0          100        100        OK
C0  Power-Off Retract Count        0          200        200        OK
C1  Emergency Retract Cycle Ct     0          200        200        OK
C2  Temperature Celsius            0          104        93         OK
C4  Reallocated Event Count        0          200        200        OK
C5  Current Pending Sector         0          200        200        OK
C6  Offline Uncorrectable          0          200        200        OK
C7  UDMA CRC Error Count           0          200        200        OK
C8  Multi Zone Error Rate          0          200        200        OK
-------------------------------------------------------------------------------


[/FONT]

---

