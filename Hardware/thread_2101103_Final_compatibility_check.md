---
title: "Final compatibility check"
date: 2013-01-03
forum: Hardware
---

### Post by heen on 2013-01-03
I want to put together the following hardware:

Intel Core i3 3225 2x 3.30GHz So.1155 BOX
ASRock Z77 Pro4-M Intel Z77 So.1155 Dual Channel DDR3 mATX Retail
16GB Corsair Vengeance LP Black DDR3-1600 DIMM CL10 Dual Kit
	
1024MB Asus GeForce GTX 650 Ti DirectCU II Aktiv PCIe 3.0 x16

60GB Corsair Force GT Series CSSD-F60GBGT-BK 2.5" SATA 6Gb/s MLC synchron
2000GB WD Green WD20EZRX 64MB 3.5" SATA 6Gb/s
Samsung SN-506AB Blu-ray Disc Writer SATA 1.5Gb/s 

I hope to enjoy Ubuntu on that machine but it has been a while since my last build so I prefer to ask before I run into some problems.

1) I read about some WD Intellipark problems. Is it still actual? Can be fixed?

2) Many motherboards offers Lucid Virtu Universal MVP. Does it work on Ubuntu or at least does not harm? If not is there any alternative? I like the idea of using GPU just when necessary.

3) Can you spot any obvious compatibility problems with that hardware? Any other suggestions?

Thank you!

---

### Post by bjfreeman on 2013-02-05
> **heen said:**
> I want to put together the following hardware:
 
 
2000GB WD Green WD20EZRX 64MB 3.5" SATA 6Gb/s
 
1) I read about some WD Intellipark problems. Is it still actual? Can be fixed?
  

 
 
Hey,
 
Have you any issues with the WD20EZRX drive? Did you disable the Intellipark?
I'm Planning on using these drives.
 
Cheers

---

### Post by heen on 2013-02-09
Hi,

I think everything is fine out of the box.

After 316h of work I have 1159 load cycles. I have read that disk can hold 1M load cycles. If so 316h * (1M/1159) gives around 30 years of work. Details follow.

Thanks for reminding!

```


Device Model:     WDC WD20EZRX-00DC0B0
Serial Number:    WD-WMC1T1557560
LU WWN Device Id: 5 0014ee 003802ddb
Firmware Version: 80.00A80
User Capacity:    2,000,398,934,016 bytes [2,00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ACS-2 (revision not indicated)
Local Time is:    Sat Feb  9 12:25:51 2013 CET
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   179   178   021    Pre-fail  Always       -       6033
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       55
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       316
 10 Spin_Retry_Count        0x0032   100   253   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       55
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       28
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       1159
194 Temperature_Celsius     0x0022   117   109   000    Old_age   Always       -       33
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

```

---

### Post by andyhelloween on 2013-02-11
> **heen said:**
> I want to put together the following hardware:
Intel Core i3 3225 2x 3.30GHz So.1155 BOX
ASRock Z77 Pro4-M Intel Z77 So.1155 Dual Channel DDR3 mATX Retail
 
Hi heen,
 
Sorry for hi-jacking your thread. Could you please confirm if that motherboard worked out of the box with Ubuntu? Even with the UEFI Bios?
 
Thanks!

---

### Post by heen on 2013-02-12
> **andyhelloween said:**
> 
Sorry for hi-jacking your thread. 


Thanks for asking. I am happy to share my experience.

> **andyhelloween said:**
> 
Could you please confirm if that motherboard worked out of the box with Ubuntu? Even with the UEFI Bios?


Yes, it worked out of the box. I wasn't aware I have UEFI Bios :) I also haven't try to do any OC.

My final configuration is

Intel Core i5 3570K 4x 3.40GHz So.1155 BOX
ASRock Z77 Extreme4-M Intel Z77 So.1155 Dual Channel DDR3 mATX R
16GB Corsair Vengeance Black DDR3-1600 DIMM CL9 Dual Kit

60GB Corsair Force GT Series CSSD-F60GBGT-BK 2.5" (6.4cm) S
2000GB WD Green WD20EZRX 64MB 3.5" (8.9cm) SATA 6Gb/s
Samsung SN-506AB Blu-ray Disc Writer SATA 1.5Gb/s

I resigned from GPU and upgraded CPU to HD4000 as I don't play any killer games. Everything worked out smoothly.

Cheers!

---

