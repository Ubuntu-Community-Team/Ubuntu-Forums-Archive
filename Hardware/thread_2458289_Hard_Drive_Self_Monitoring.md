---
title: "Hard Drive Self Monitoring"
date: 2021-02-20
forum: Hardware
---

### Post by manikinxvx on 2021-02-20
I understand what "Hard drive self monitoring has reported that a parameter has exceeded its normal operating range... " means and that it can indicate potential critical failure of a drive. What I'm wondering is if there is a way to see what parameter is out of range so I determine if I should worry about it or not.

If this question has already been asked, I apologize.


--manikinxvx

---

### Post by TheFu on 2021-02-20
Use **smartctl**.  Search these forums for more info.

---

### Post by DuckHook on 2021-02-20
In fairness, smartctl output can be hard to parse. Even successfully parsed, it can be hard to understand.

[list=1]
[*]Not all HDD OEMs adhere to good output etiquette. Seagate for example are awful. They use the various fields for their own obscure internal codes.
[*]smartctl can be misleading, especially that predicted disk failure stuff. However, because it is so painful to experience actual failure, its messages should not be ignored. When it comes to HDDs, better safe than sorry.
[*]The most accurate way to test a HDD is to use smartctl's testing routines, especially the long test.
[*]Purely my own bias, but my attitude to HDDs is pretty intolerant: if I have even the smallest reason for doubt, I will no longer trust that HDD. Too many bad experiences earlier in life from being too sanguine with bad rust. New drives aren't expensive these days (unless you are going for enterprise&#8209;level monster drives). Better safe than sorry.
[/list]
Here's a typical output comparison from two similarly very old and beat up drives. They both have issues, but how to tell which are big and which are little? I've highlighted fields it's important to pay attention to:

**More Trustworthy Drive:**
```
duckhook@xxxxxx:~$ sudo smartctl -A /dev/sdd
smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.4.0-65-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   046    Pre-fail  Always       -       131614
  2 Throughput_Performance  0x0004   100   100   000    Old_age   Offline      -       21954560
  3 Spin_Up_Time            0x0003   100   100   025    Pre-fail  Always       -       2
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       4090
**[COLOR="#0000FF"]  5 Reallocated_Sector_Ct   0x0033   100   100   024    Pre-fail  Always       -       0 (2000 0)[/COLOR]**
  7 Seek_Error_Rate         0x000e   100   100   000    Old_age   Always       -       3940
  8 Seek_Time_Performance   0x0004   100   100   000    Old_age   Offline      -       0
  9 Power_On_Hours          0x0032   005   005   000    Old_age   Always       -       47586
 10 Spin_Retry_Count        0x0012   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       4075
191 G-Sense_Error_Rate      0x0012   100   100   000    Old_age   Always       -       34
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       48
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       31 (Min/Max 14/49)
[COLOR="#0000FF"]**195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       0**[/COLOR]
**[COLOR="#0000FF"]196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0 (0 6981)[/COLOR]**
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
[COLOR="#0000FF"]**198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0**[/COLOR]
**[COLOR="#0000FF"]199 UDMA_CRC_Error_Count    0x003e   200   253   000    Old_age   Always       -       0[/COLOR]**
200 Multi_Zone_Error_Rate   0x000e   100   100   000    Old_age   Always       -       12882
201 Soft_Read_Error_Rate    0x0010   100   100   000    Old_age   Offline      -       0
203 Run_Out_Cancel          0x0002   100   100   000    Old_age   Always       -       1533274686111
225 Load_Cycle_Count        0x0032   096   096   000    Old_age   Always       -       8590028514
240 Head_Flying_Hours       0x003e   200   200   000    Old_age   Always       -       0
254 Free_Fall_Sensor        0x0032   100   100   000    Old_age   Always       -       2

```

**Less Trustworthy Drive:**
```
duckhook@xxxxxx:~$ sudo smartctl -A /dev/sda
smartctl 7.1 2019-12-30 r5022 [aarch64-linux-5.4.0-1028-raspi] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   092   046    Pre-fail  Always       -       101921
  2 Throughput_Performance  0x0004   100   100   000    Old_age   Offline      -       39190528
  3 Spin_Up_Time            0x0003   100   100   025    Pre-fail  Always       -       1
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       985
**[COLOR="#0000FF"]  5 Reallocated_Sector_Ct   0x0033   100   100   024    Pre-fail  Always       -       71 (1948 52)[/COLOR]**
  7 Seek_Error_Rate         0x000e   100   100   000    Old_age   Always       -       675
  8 Seek_Time_Performance   0x0004   100   100   000    Old_age   Offline      -       0
  9 Power_On_Hours          0x0032   013   013   000    Old_age   Always       -       43951
 10 Spin_Retry_Count        0x0012   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       860
191 G-Sense_Error_Rate      0x0012   100   100   000    Old_age   Always       -       34
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       58
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       27 (Min/Max 20/53)
[COLOR="#0000FF"]**195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       7578**[/COLOR]
**[COLOR="#0000FF"]196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       29 (18 6891)[/COLOR]**
197 Current_Pending_Sector  0x0012   098   095   000    Old_age   Always       -       3
[COLOR="#0000FF"]**198 Offline_Uncorrectable   0x0010   091   091   000    Old_age   Offline      -       19**[/COLOR]
**[COLOR="#0000FF"]199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0[/COLOR]**
200 Multi_Zone_Error_Rate   0x000e   100   099   000    Old_age   Always       -       22419
201 Soft_Read_Error_Rate    0x0010   100   100   000    Old_age   Offline      -       0
203 Run_Out_Cancel          0x0002   100   100   000    Old_age   Always       -       3728048653857
225 Load_Cycle_Count        0x0032   099   099   000    Old_age   Always       -       25731
240 Head_Flying_Hours       0x003e   200   200   000    Old_age   Always       -       0
```
Having any number but 0 ("zero") in these fields is a troubling sign.

Also try:```
sudo smartctl -H /dev/sd[X]
```&#8230;where [X] is your drive. If the result is anything other than ***PASSED***, back up everything immediately and don't use that drive.

Smartctl has too many reporting/testing options to count. Its ***man*** page is very helpful and not too arcane. This link might also help: [https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

---

