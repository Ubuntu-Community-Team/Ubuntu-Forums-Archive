---
title: "Strange noise on shutdown with Feisty."
date: 2007-10-07
forum: Hardware &amp; Laptops
---

### Post by whitefort on 2007-10-07
Hi,

Ever since one of the recent updates, my Lenovo is making a strange sound on shutdown, just as the machine switches off.  It's hard to describe - a sort of electronic 'pop' sound - but it really doesn't sound very healthy.  It does seem to be related to Feisty, because it only started since the update, and also I've tried running the computer with a Puppy \Linux live CD, and then I can shutdown without the sound.

If anyone else has experienced this and knows what's doing it, I have two questions:

Is this something I should be worried about - iis it hurting my machine?
and
What's causing it?

Thanks!

---

### Post by dinub1 on 2007-10-07
> **whitefort said:**
> Hi,

Ever since one of the recent updates, my Lenovo is making a strange sound on shutdown, just as the machine switches off.  It's hard to describe - a sort of electronic 'pop' sound - but it really doesn't sound very healthy.  It does seem to be related to Feisty, because it only started since the update, and also I've tried running the computer with a Puppy \Linux live CD, and then I can shutdown without the sound.

If anyone else has experienced this and knows what's doing it, I have two questions:

Is this something I should be worried about - iis it hurting my machine?
and
What's causing it?[http://ubuntuforums.org/showthread.php?t=566072&highlight=is+gutsy+killing+laptops](http://ubuntuforums.org/showthread.php?t=566072&highlight=is+gutsy+killing+laptops)

Thanks!

Yes, there seems to be a problem runing latest Ubuntu on some laptops. Pls. read[ [COLOR="Red"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=566072&highlight=is+gutsy+killing+laptops").

---

### Post by nick_h on 2007-10-07
Yes, it probably is this problem.  The OP can check with the following command:
```
sudo smartctl --device=ata --attributes /dev/sda
```
(assuming the hdd is /dev/sda)
If the Power-Off_Retract_Count increases by 1 after each shutdown then it is the same problem.
I found that [this post](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810/comments/60) in bug #67810 solved the problem for me.

---

### Post by whitefort on 2007-10-08
Thanks for the replies, guys - and thanks especially for the 'fix', which has solved the problem on my machine.

But...  I'm shocked beyond words!!  (well, nearly :))

If our beloved Ubuntu has a bug that can break a harddrive, why isn't this better publicized?  Why isn't there a big red banner at the top of the forum saying: 'WARNING!!!  LAPTOP OWNERS READ THIS NOW!!!'?

Or why didn't the fix come automatically in one of the regular update thingies?

I mean, really - all sorts of minor things are auto-fixed, but when it's a bug that could physically wreck my laptop I find out about it almost by accident?  I love Ubuntu dearly, but something like this is a major confidence-shaker.

Anyway, the fix works, so no harm done - though I feel for anyone who won't realise there's a problem until it's too late.

Just out of curiosity, the command:  sudo smartctl --device=ata --attributes /dev/sda

gives me a 'command not found' message.  Do I need to install something else for it to work?

But once again, and very seriously MANY thanks, guys - I love Ubuntu, but I love my laptop more - thank you for the life-saving fix!

---

### Post by dinub1 on 2007-10-08
You are very welcome :)


[I][COLOR="Navy"]Just out of curiosity, the command: sudo smartctl --device=ata --attributes /dev/sda
gives me a 'command not found' message. Do I need to install something else for it to work?[/COLOR][/I]

Yes, you need to install a program called "smarttools". It does not come installed by default in Ubuntu. Type "smart" in Synaptic and you shall see.

---

### Post by nick_h on 2007-10-08
You need smartmon tools:
```
sudo apt-get install smartmontools
```
It would be interesting to see what your power-off reftract count is.

There was a thread started back in July called [Ubuntu is killing your hdd!](http://ubuntuforums.org/showthread.php?t=508576) which contains a discussion about how damaging the emergency retract is.  Although it is obviously not a good thing I suspect that it isn't too bad.

---

### Post by dinub1 on 2007-10-08
It is 86. Look at the previous thread on the same issue. I have installed smarttools and therefore I could use the smartctl command. I am now under windows so I cannot post directly but it is 86 and it remained the same in days, after several shutdowns.

This issue apparently affects only SATA drives not PATA. Mine is a regular (IDE) PATA HDD. I do not hear clicks.

---

### Post by dinub1 on 2007-10-08
*[COLOR="Navy"]It would be interesting to see what your power-off retract count is.[/COLOR]*

Here it is:

dinu@ubuntu710:~$ sudo smartctl --device=ata --attributes /dev/hda
[sudo] password for dinu:
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   046    Pre-fail  Always       -       103644
  2 Throughput_Performance  0x0005   100   100   030    Pre-fail  Offline      -       26345472
  3 Spin_Up_Time            0x0003   100   100   025    Pre-fail  Always       -       1
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       392
  5 Reallocated_Sector_Ct   0x0033   100   100   024    Pre-fail  Always       -       8589934592000
  7 Seek_Error_Rate         0x000f   100   100   047    Pre-fail  Always       -       1805
  8 Seek_Time_Performance   0x0005   100   100   019    Pre-fail  Offline      -       0
  9 Power_On_Seconds        0x0032   087   087   000    Old_age   Always       -       6862h+05m+14s
 10 Spin_Retry_Count        0x0013   100   100   020    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       392
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       86
193 Load_Cycle_Count        0x0032   085   085   000    Old_age   Always       -       303150
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       43 (Lifetime Min/Max 18/52)
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       760
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       456392704
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000f   100   100   060    Pre-fail  Always       -       21554
203 Run_Out_Cancel          0x0002   100   100   000    Old_age   Always       -       3728048914469

dinu@ubuntu710:~$

---

### Post by dinub1 on 2007-10-08
> **nick_h said:**
> You need smartmon tools:
```
sudo apt-get install smartmontools
```
It would be interesting to see what your power-off reftract count is.

There was a thread started back in July called [Ubuntu is killing your hdd!](http://ubuntuforums.org/showthread.php?t=508576) which contains a discussion about how damaging the emergency retract is.  Although it is obviously not a good thing I suspect that it isn't too bad.


Ooops.. it is smartmontools :) I am sorry

---

### Post by nick_h on 2007-10-08
Mine is 156 - although it is an old drive and some of these will not be due to the Feisty bug.

My drive is a PATA and it was affected.  I think the bug occurred when they changed to a scsi driver in Feisty and the drive became /dev/sda rather than /dev/hda that it is with Dapper.

---

### Post by dinub1 on 2007-10-08
> **nick_h said:**
> Mine is 156 - although it is an old drive and some of these will not be due to the Feisty bug.

My drive is a PATA and it was affected.  I think the bug occurred when they changed to a scsi driver in Feisty and the drive became /dev/sda rather than /dev/hda that it is with Dapper.

OK... it may be... for some reason I thought I saw a thread mentioning that this bug affects only the SATA drive.

But you know ? On desktops, that parameter does not show at all. This is a 3-4 days new SATA-2 HDD on this desktop. Look what it reports.

dinu@Ubuntu710PC:~$ sudo smartctl --device=ata --attributes /dev/sda
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   105   100   006    Pre-fail  Always       -       9508032
  3 Spin_Up_Time            0x0003   098   098   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       13
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   100   253   030    Pre-fail  Always       -       289256
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       20
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       13
187 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
189 Unknown_Attribute       0x003a   100   100   000    Old_age   Always       -       0
190 Temperature_Celsius     0x0022   068   057   045    Old_age   Always       -       538247200
194 Temperature_Celsius     0x0022   032   043   000    Old_age   Always       -       32 (Lifetime Min/Max 0/21)
195 Hardware_ECC_Recovered  0x001a   078   067   000    Old_age   Always       -       88085127
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

dinu@Ubuntu710PC:~$

So that parameter  for disk shutdown is in effect (apparently) on laptops only.

---

### Post by nick_h on 2007-10-08
My machine is a laptop with a Hitachi drive.  I would expect that the SMART standard is implemented slightly differently between manufacturers.  What make is your drive?

There is a [wiki](http://en.wikipedia.org/wiki/Self-Monitoring%2C_Analysis%2C_and_Reporting_Technology) page which gives some interesting information.

---

### Post by dinub1 on 2007-10-08
> **nick_h said:**
> My machine is a laptop with a Hitachi drive.  I would expect that the SMART standard is implemented slightly differently between manufacturers.  What make is your drive?

There is a [wiki](http://en.wikipedia.org/wiki/Self-Monitoring%2C_Analysis%2C_and_Reporting_Technology) page which gives some interesting information.

It can be. My laptop HDD is a Fujitsu made, 100 GB 5400 RPM, I upgraded it myself approx 1 yr ago from a 40 GB 4200 RPM IBM drive which same with HP Pavilion laptop. I ran out of space cause I am running dual boot Windows XP Home and Ubuntu.

---

