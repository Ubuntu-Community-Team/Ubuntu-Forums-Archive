---
title: "Problems with my hard disk"
date: 2009-12-17
forum: Hardware
---

### Post by Mr.Eslam on 2009-12-17
i use ubuntu 9.10 on my Hp 550 laptop , 160 Gib Hitatchi Hard disk

im facing a problem that the disk utility says that the hard disk is failing and have many bad sectors.

im trying using

```
sudo fdisk /dev/sda
```but it says

```
The number of cylinders for this disk is set to 19457.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Unable to seek on /dev/sda

```so i have installed an application called gparted , but it can c 149 Gib of Unallocated space , don't know how.

Then i have installed GsmartControl and it gives some errors
```

Complete error log:

SMART Error Log Version: 1
ATA Error Count: 11 (device log contains only the most recent five errors)
    CR = Command Register [HEX]
    FR = Features Register [HEX]
    SC = Sector Count Register [HEX]
    SN = Sector Number Register [HEX]
    CL = Cylinder Low Register [HEX]
    CH = Cylinder High Register [HEX]
    DH = Device/Head Register [HEX]
    DC = Device Command Register [HEX]
    ER = Error register [HEX]
    ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 11 occurred at disk power-on lifetime: 1853 hours (77 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 0c f1 88 a3 ea  Error: UNC 12 sectors at LBA = 0x0aa388f1 = 178489585

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 3f be 88 a3 e0 00      01:14:59.500  READ DMA EXT
  25 00 04 ba 88 a3 e0 00      01:14:59.500  READ DMA EXT
  25 00 3f 7b 88 a3 e0 00      01:14:59.500  READ DMA EXT
  25 00 3f 3c 88 a3 e0 00      01:14:59.500  READ DMA EXT
  25 00 3f fd 87 a3 e0 00      01:14:59.500  READ DMA EXT

Error 10 occurred at disk power-on lifetime: 58 hours (2 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 04 2b e4 e5 e1  Error: UNC 4 sectors at LBA = 0x01e5e42b = 31843371

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 27 e4 e5 e0 00      00:05:36.700  READ DMA EXT
  25 00 08 1f e4 e5 e0 00      00:05:36.700  READ DMA EXT
  25 00 08 17 e4 e5 e0 00      00:05:36.700  READ DMA EXT
  25 00 08 0f e4 e5 e0 00      00:05:36.700  READ DMA EXT
  25 00 08 07 e4 e5 e0 00      00:05:36.700  READ DMA EXT

Error 9 occurred at disk power-on lifetime: 58 hours (2 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 8c 2b e4 e5 e1  Error: UNC 140 sectors at LBA = 0x01e5e42b = 31843371

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 00 b7 e3 e5 e0 00      00:05:32.100  READ DMA EXT
  25 00 00 b7 e2 e5 e0 00      00:05:32.100  READ DMA EXT
  25 00 00 b7 e1 e5 e0 00      00:05:32.100  READ DMA EXT
  25 00 00 b7 e0 e5 e0 00      00:05:32.100  READ DMA EXT
  25 00 00 b7 df e5 e0 00      00:05:32.100  READ DMA EXT

Error 8 occurred at disk power-on lifetime: 57 hours (2 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 04 2b e4 e5 e1  Error: UNC at LBA = 0x01e5e42b = 31843371

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  29 00 08 27 e4 e5 e0 00      00:01:36.800  READ MULTIPLE EXT
  29 00 08 1f e4 e5 e0 00      00:01:36.700  READ MULTIPLE EXT
  29 00 08 17 e4 e5 e0 00      00:01:36.700  READ MULTIPLE EXT
  29 00 08 0f e4 e5 e0 00      00:01:36.700  READ MULTIPLE EXT
  29 00 08 07 e4 e5 e0 00      00:01:36.700  READ MULTIPLE EXT

Error 7 occurred at disk power-on lifetime: 57 hours (2 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 0c 2b e4 e5 e1  Error: UNC at LBA = 0x01e5e42b = 31843371

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  29 00 00 37 e3 e5 e0 00      00:01:27.700  READ MULTIPLE EXT
  29 00 00 37 e2 e5 e0 00      00:01:27.600  READ MULTIPLE EXT
  29 00 00 37 e1 e5 e0 00      00:01:27.500  READ MULTIPLE EXT
  29 00 00 37 e0 e5 e0 00      00:01:27.500  READ MULTIPLE EXT
  29 00 00 37 df e5 e0 00      00:01:27.400  READ MULTIPLE EXT
```also

```
Reallocated Sector Count 
Failed:Never 
norm-ed value 100
worst 100
threshold 5
Raw Value 196611

```Besides

```
Reallocated Event Count
Failed:Never 
norm-ed value 100
worst 100
threshold 0
Raw Value 3

```
Note : The GsmartControl still says that Basic Health Test : Passed.
I Hope anyone could help me to solve these problems coz i want to create other partitions on the free space i have.

---

### Post by andrewkevin on 2010-04-01
Start the SeaMap.exe software
Set the option by typing SD and then press enter
Press 1 then 0 or 1 to select drive
Then press 2 and there will be a option (Y/N) press n for No
Press Esc button one to go back to command line
Type FD
Type y for yes the Hdd will format [Low Level Format] the whole disk and removes bad sectors and partitions
Now the computer has to be restarted, Restart your computer
Partition your Hdd using fdisk and then format all partitions now have have completely removed all bad sectors from your hard disk

---

