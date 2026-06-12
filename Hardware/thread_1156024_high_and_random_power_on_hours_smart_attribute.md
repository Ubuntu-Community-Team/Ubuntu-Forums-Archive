---
title: "high and random power_on_hours smart attribute"
date: 2009-05-11
forum: Hardware
---

### Post by Language on 2009-05-11
I'm not having any hdd issues at the moment, but I recently obtained this machine from eBay so I was curious how much the hdd had been utilized prior to my purchase.

The laptop is a Lenovo Thinkpad X41 Tablet, the hdd is a HTC426060G8CE00 (ATA) which mounts on /dev/sda1.

Regardless of whether or not i use the "-d ata" flag, the power_on_hours come up as a large, seemingly random number (the number changes every time I run smartctl!) while the other numbers seem more reasonable (e.g. 150 power cycles).

Some sample values: 8847632662132, 13035225775734, 16965120851574

The following is the output of **smartctl -a -d ata /dev/sda1**:

ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000d   100   100   050    Pre-fail  Offline      -       0
  2 Throughput_Performance  0x0005   100   100   050    Pre-fail  Offline      -       22840
  3 Spin_Up_Time            0x0006   100   100   000    Old_age   Always       -       0
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       248
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   100   100   050    Pre-fail  Always       -       891
  8 Seek_Time_Performance   0x0005   100   100   050    Pre-fail  Offline      -       1216
  **9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       5184025558638**
 10 Spin_Retry_Count        0x0013   100   100   050    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       150
191 G-Sense_Error_Rate      0x000a   100   079   000    Old_age   Always       -       302056002
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       9
193 Load_Cycle_Count        0x0032   098   098   000    Old_age   Always       -       292041016329
194 Temperature_Celsius     0x0022   100   084   000    Old_age   Always       -       33 (Lifetime Min/Max 12/42)
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       1
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0013   100   100   050    Pre-fail  Always       -       0
201 Soft_Read_Error_Rate    0x0012   100   100   000    Old_age   Always       -       0
223 Load_Retry_Count        0x0012   100   100   000    Old_age   Always       -       0
230 Head_Amplitude          0x0032   100   100   000    Old_age   Always       -       9083855857867
250 Read_Error_Retry_Rate   0x000a   100   100   000    Old_age   Always       -       349


Any ideas? Thanks in advance! :o

---

### Post by MBellator on 2009-05-24
Don't worry about the 9th attribute, "there is no error so the message can be ignored" ( [https://twiki.cern.ch/twiki/bin/view/FIOgroup/DiskPrbSmart](https://twiki.cern.ch/twiki/bin/view/FIOgroup/DiskPrbSmart) ).

Here's what this output does say:

5   Reallocated_Sector_Ct  0x0033 100 100 010 Pre-fail Always - "0"
197 Current_Pending_Sector 0x0032 100 100 000 Old_age  Always - "0"
198 Offline_Uncorrectable  0x0010 100 100 000 Old_age  Offline - "0"
Note the "0"s -- if they weren't zeroes, you'd need to replace your hard drive ASAP.  As for the age of the drive:


sudo smartctl -t short /dev/sda


and take a 10min, or however long it says to wait for break from the computer.  Then this will print only the most recent result:

smartctl -l selftest /dev/sda | sed '7q'

The LifeTime(hours) column is, of course, what you're interested in.  It's probably also worth;

sudo smartctl -t long /dev/sda

wait for it to complete

smartctl -a /dev/sda | less

There are other tests you can do.  "man smartctl" for more info.  Also, I've heard that certain bonnie++ and iozone benchmarks are good for stress-testing hard drives.

'hope this helps!
Nick

---

