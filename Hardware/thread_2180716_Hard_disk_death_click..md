---
title: "Hard disk death click."
date: 2013-10-14
forum: Hardware
---

### Post by bvstoichkov on 2013-10-14
Hello,
I am fairly new to Linux and Ubuntu. Have been using them for few months only. The problem I have is Ubuntu killed my old hard drive. I wasn't quite sure tough. I checked it off to maybe it being 5-ish year old laptop drive. 

Now I have a new one. This one has 300-400 hours usage if I remember correctly. I was hearing a clicking noise from the first day I logged in Ubuntu. I didn't think much of it at start. One day my X.org crashed and my paranoia kicked in high gear. I started searching on the internet about hard disk clicking (the clicking comes when I open a program or do some operation, loading). I did the cycles to hour usage check which everyone seems to recommend and it seemed fine with 11 ratio. I said to my self that this clicking(it sounds more like a faint chirping sound) is not the one people were talking about. Until today.

While I was watching some TV show I heard the dreaded click of death. The writing head was hitting its most left and right positions. I minimized my video and tried to click the shutdown button but the menu did not pop. I hold down the shutdown button to stop the laptop. I am writing this from Windows 7 right now. There is no chirping here there is no death click either. I am afraid to log in under Ubuntu for something worse might happen.

TL: DNR
Clicking sound when something is loading - starting program, using program, whenever Ubuntu is working basically. The sound is really more like faint chirping or faint scratching maybe(The room must be quite to hear it). Today click of death for few seconds before I hard shutdown the laptop. No such problems under Windows right now.


I am on laptop Acer aspire 6920G, hard disk [FONT=arial]Western Digital WD5000LPVT 60G33T0 ATA.
[/FONT]OS - Ubuntu 13.04. I think the hddparam apm was set 254 if I remember correctly from last time. Cycles to time used ration was 11 last I checked.(The information is from before 2-3 weeks.


Do you guys think I could get my disk changed as it's still under guarantee, although technically it is working under Windows. I would provide any other information as long as you instruct me how to get it. It would be great if I don't have to log under Ubuntu to get that information. I am willing to try but if I hear the death click again I'll just bolt out of it. You could give me links to solutions but I would have probably read most of them.

---

### Post by Yellow Pasque on 2013-10-14
What you're probably referring to is the "Intellipark" feature of modern WD drives. There's actually a Windows utility (google wdidle3.exe) to turn Intellipark off, so you should try that and see if it stops the noise.

> Do you guys think I could get my disk changed as it's still under guarantee, although technically it is working under Windows.
It depends on where you got it. You may be able to return it outright and pay a restocking fee if you want to get a different model. As far as replacing the drive with another one of the same model, that's probably a dead end, as a new one will just display the same behavior.

---

### Post by bvstoichkov on 2013-10-14
Thanks for the quick reply. I found wdidle3.exe and disabled the intelliparking. I am currently under Ubuntu but I still hear that scratching sound when I load the system with some task (when it is not that busy it clicks once in a while).
Here is what smartctl -A gives me. I cant say if it is good or bad. Have in mind that my hard disk is not in database whatever that may mean.
I can see that my load_cycle_count/power_on = 12 that means it has increased by 1 for 2 weeks. Dunno if that matters.
```

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   154   151   021    Pre-fail  Always       -       1258
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       210
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002f   200   200   051    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       426
 10 Spin_Retry_Count        0x0033   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       210
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0033   100   100   097    Pre-fail  Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   054   043   040    Old_age   Always       -       46 (Min/Max 45/46)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       13
193 Load_Cycle_Count        0x0032   199   199   000    Old_age   Always       -       5144
194 Temperature_Celsius     0x0022   097   086   000    Old_age   Always       -       46
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0009   100   253   051    Pre-fail  Offline      -       0



```

---

### Post by Yellow Pasque on 2013-10-14
My drives click once in a wile when they're idle. I don't think it's a "click of death" (or they would have died a long time ago). As for the scratching sound under load and why it doesn't do it in Windows, I'm not sure what to tell you.

```
Have in mind that my hard disk is not in database whatever that may mean.
```
It's not a big deal, but there is a command to fetch the latest database version in case they've added your drive:
```
sudo update-smart-drivedb
```

---

### Post by bvstoichkov on 2013-10-14
Thanks any way for the speared time. By "click of death" I do mean that I heard the real thing. The writing head was hitting the utmost left position and the right one two(that is how it sounded not some faint clicks from parking). It might not be because it is dying but because of some bad sectors or some error. I did read that hdparm apm 254 was not working for every disk and I might try 255 and see what happens.

---

