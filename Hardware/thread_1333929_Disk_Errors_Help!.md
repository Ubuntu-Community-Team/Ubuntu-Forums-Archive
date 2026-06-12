---
title: "Disk Errors Help!"
date: 2009-11-21
forum: Hardware
---

### Post by Rich_S on 2009-11-21
I just upgraded from 9.04 to 9.10 today.

Palimpsest is reporting Disk Has Many Bad Sectors.

A little searching revealed some known bugs with Palimpsest. So I installed smartmontools.

Output of tests is below:

----------------------------------------------
rich@rich-desktop:~$ sudo smartctl -l selftest /dev/sda
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [[COLOR=#444444]http://smartmontools.sourceforge.net/[/COLOR]]("http://smartmontools.sourceforge.net/")

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num Test_Description Status Remaining LifeTime(hours) LBA_of_first_error
# 1 Extended offline Completed without error 00% 17406 -
# 2 Short offline Completed without error 00% 17403 -




rich@rich-desktop:~$ sudo smartctl -l error /dev/sda
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [[COLOR=#444444]http://smartmontools.sourceforge.net/[/COLOR]]("http://smartmontools.sourceforge.net/")

=== START OF READ SMART DATA SECTION ===
SMART Error Log Version: 1
No Errors Logged



rich@rich-desktop:~$ sudo smartctl -A /dev/sda
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [[COLOR=#444444]http://smartmontools.sourceforge.net/[/COLOR]]("http://smartmontools.sourceforge.net/")

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME FLAG VALUE WORST THRESH TYPE UPDATED WHEN_FAILED RAW_VALUE
1 Raw_Read_Error_Rate 0x000f 117 094 006 Pre-fail Always - 159933204
3 Spin_Up_Time 0x0003 094 093 000 Pre-fail Always - 0
4 Start_Stop_Count 0x0032 100 100 020 Old_age Always - 97
5 Reallocated_Sector_Ct 0x0033 100 100 036 Pre-fail Always - 0
7 Seek_Error_Rate 0x000f 083 060 030 Pre-fail Always - 201963397
9 Power_On_Hours 0x0032 081 081 000 Old_age Always - 17406
10 Spin_Retry_Count 0x0013 100 100 097 Pre-fail Always - 0
12 Power_Cycle_Count 0x0032 099 099 020 Old_age Always - 1248
187 Reported_Uncorrect 0x0032 100 100 000 Old_age Always - 0
189 High_Fly_Writes 0x003a 100 100 000 Old_age Always - 0
190 Airflow_Temperature_Cel 0x0022 055 046 045 Old_age Always - 45 (Lifetime Min/Max 31/49)
194 Temperature_Celsius 0x0022 045 054 000 Old_age Always - 45 (0 22 0 0)
195 Hardware_ECC_Recovered 0x001a 055 051 000 Old_age Always - 194793134
197 Current_Pending_Sector 0x0012 001 001 000 Old_age Always - 4294967295
198 Offline_Uncorrectable 0x0010 001 001 000 Old_age Offline - 4294967295
199 UDMA_CRC_Error_Count 0x003e 200 200 000 Old_age Always - 0
200 Multi_Zone_Error_Rate 0x0000 100 253 000 Old_age Offline - 0
202 TA_Increase_Count 0x0032 100 253 000 Old_age Always - 0
-------------------------

The Current_Pending_Sector and Offline_Unrecoverable raw values really have me worried.

Thoughts?

---

### Post by Rich_S on 2009-11-22
[SIZE=2]Downloaded the Seagate Seatools Disk Diagnostic Utilities and created a bootable CD.

Ran the short version and long version and and both reported: "SMART Is Supported And ENABLED. SMART Has NOT Been Tripped. No Errors Found".[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]WTF????!!!!![/SIZE]

---

