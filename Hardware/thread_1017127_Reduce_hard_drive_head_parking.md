---
title: "Reduce hard drive head parking?"
date: 2008-12-20
forum: Hardware
---

### Post by theevilhamster on 2008-12-20
Im starting to get worried about the amount of times ubuntu is parking my hard rives head as i am now up 218427 load cycles.

here is my S.M.A.R.T. info for now.

```
rob@linux:~$ sudo smartctl -A /dev/sda
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   050    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   050    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0027   100   100   001    Pre-fail  Always       -       578
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       3321
  5 Reallocated_Sector_Ct   0x0033   100   100   050    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   050    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   050    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   094   094   000    Old_age   Always       -       2572
 10 Spin_Retry_Count        0x0033   166   100   030    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       3032
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       372
193 Load_Cycle_Count        0x0032   079   079   000    Old_age   Always       -       218427
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       36 (Lifetime Min/Max 9/46)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       1
220 Disk_Shift              0x0002   100   100   000    Old_age   Always       -       152
222 Loaded_Hours            0x0032   096   096   000    Old_age   Always       -       1899
223 Load_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
224 Load_Friction           0x0022   100   100   000    Old_age   Always       -       0
226 Load-in_Time            0x0026   100   100   000    Old_age   Always       -       400
240 Head_Flying_Hours       0x0001   100   100   001    Pre-fail  Offline      -       0


```

it has increased by about 6 as i was typing this!

i have tried using hdparm to reduce the sleep time but it hasn't worked :(.

I heard recently that this used to be a bug, but it has been fixed.

Some help will be greatly appreciated, or should i not worry? my laptop is only 2 years old in january:(.

edit: now its gone up another 11 as i typed the last bit:|

---

### Post by trapgate on 2008-12-20
It sounds like the current spindown time is set very low, and I'm not sure why that would be. But you should be able to fix your problem by editing /etc/hdprarm.conf and setting your own timeouts there. I found a page with some instructions on doing this:

[http://www.ubuntukungfu.org/blog/2008/09/9-tips-for-ubuntu-notebook-users/](http://www.ubuntukungfu.org/blog/2008/09/9-tips-for-ubuntu-notebook-users/)

Hope it helps!

---

### Post by theevilhamster on 2008-12-20
For some reason when i tried running the hdparm command earlier, it didnt change that :|.

Thanks a lot, i have edited the file, and hope it parks my heads less. If only i had caught it earlier then my drive would be a little less dead but its too late for that.

Anyway thanks loads for the help, and quick reply, greatly appreciated, you may have just saved my drive.

EDIT!: Just restarted to make sure all is ok; that didnt work either:'( WTF is wrong with my drive!

---

### Post by trapgate on 2008-12-21
Hmm. If you do:

sudo hdparm -S 0 /dev/sda

does that help? That should disable spindown completely for the drive (it won't change the default in /etc/hdparm.conf, so it won't persist across boots, but it's a good way to quickly check whether hdparm is the reason your drive is spinning down.)

---

### Post by sdennie on 2008-12-21
In your case, I wouldn't worry about it.  If your usage patterns over the last two years continue to be the same, it will be 8 years before Load_Cycle_Count could *possibly* become an issue for you.  In your case, the increased heat from using hdparm to disable this drive feature is probably much harder on the disk than leaving it on.

---

### Post by theevilhamster on 2008-12-21
HDparm doesnt work at all for some reason:(. i think that since i installed ubuntu on this machiene, it has got worse (im not sure, will check on mac os), so it may ware out quicker than 8 years. i want to stop this before it jets too bad, but thanks to all that tried to help so far:). i cant think why HDparm wont work.:confused:. any more ideas anyone?

---

### Post by trapgate on 2008-12-21
One: check the BIOS settings and see if HD spindown is configured there. If it is, that may be what's causing your problem.

---

### Post by Aearenda on 2008-12-21
You may need to turn laptop-mode on, and possibly set the hdparm settings via pm. See [https://wiki.ubuntu.com/PowerManagement](https://wiki.ubuntu.com/PowerManagement) for an overview and [this bug]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695") for gory details.

---

### Post by theevilhamster on 2008-12-22
> **trapgate said:**
> One: check the BIOS settings and see if HD spindown is configured there. If it is, that may be what's causing your problem.



I'm on a macbook, im not aware that they have BIOS settings?

---

### Post by theevilhamster on 2008-12-22
I read on one of those posts that just over 4 years is O.K. for a hdd's life, so I'm a little less worried. I will try some of the stuff on those pages. Thanks a lot everyone!:)

---

### Post by Aearenda on 2008-12-22
By the way, there may be more useful info for you at [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook) - just in case you haven't seen this.

---

