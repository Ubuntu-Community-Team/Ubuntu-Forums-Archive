---
title: "I'm quite sure it's a disk problem now!"
date: 2006-06-17
forum: Hardware &amp; Laptops
---

### Post by musther on 2006-06-17
I've been having seemingly random errors, they only occur after the machine has been turned off for a while.  For example everything is running ok, I shut down, and go to bed.  When I turn on the PC the next day, X fails to start, I log in at the command line and try startx, the output says something about x server priority being set incorrectly.  I suspect it's one of these random errors and decide to reboot.  On doing so I'm told that my root partition /dev/hdb2 contains errors, it is scanned and they are fixed, another reboot and all's well again.  Next day the root partition needs scanning on boot again (due to errors) and then everything seems to work (although the mouse is sluggish).  The next day and another scan of /dev/hdb2 is needed, then the mouse goes back to normal.  

I've had these problems ever since I used that disk (hdb) to test Windows Vista last week (after which it was repartitioned and formatted).  

Is my poor old (6-7 years) Maxtor HDD on its way out?  Is there something I should try before just going out and buying another disk?

Thanks

---

### Post by LKRaider on 2006-06-17
Try using the SMART technology to inspect your harddrive health.
Get the **smartmontools** package in Synaptic and read about it on [linuxjournal]("http://www.linuxjournal.com/article/6983").
While you are at it, install the **smart-notifier** package too, which gives SMART reports on Gnome.

Execute the long self-test ( *smartctl -t long /dev/hda* ), and if it shows any errors, get the vendor-specific [diagnostic tool]("http://www.benchmarkhq.ru/english.html?/be_hdd2.html") to fix it. This already saved one of my HD's ( it was a 4 year old Maxtor even).

Enable the daemon editing /etc/default/smartmontools and enabling the "start_smartd=yes" line, so you get SMART error reports on your dmesg log.
More smartd options can be set in the /etc/smartd.conf file.

Go to the Session preferences and add the command *smart-notifier* to the startup list to get reports inside your Gnome session.

---

### Post by musther on 2006-06-18
Hmm

```
root@dominus:/etc/default# smartctl -l error /dev/hdb
smartctl version 5.34 [i686-pc-linux-gnu] Copyright (C) 2002-5 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART Error Log Version: 1
ATA Error Count: 100 (device log contains only the most recent five errors)
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

Error 100 occurred at disk power-on lifetime: 4052 hours (168 days + 20 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 d2 e8 2f f0  Error: UNC 8 sectors at LBA = 0x002fe8d2 = 3139794

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 d2 e8 2f f0 08      00:10:49.328  READ DMA
  ca 00 08 4a 10 1e f0 08      00:10:49.264  WRITE DMA
  ca 00 38 12 10 1e f0 08      00:10:49.264  WRITE DMA
  ca 00 08 0a 5e 35 f0 08      00:10:49.264  WRITE DMA
  ca 00 08 0a 10 1e f0 08      00:10:46.144  WRITE DMA

Error 99 occurred at disk power-on lifetime: 4052 hours (168 days + 20 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 08 d2 e8 2f f0  Error: UNC 8 sectors at LBA = 0x002fe8d2 = 3139794

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 d2 e8 2f f0 08      00:10:31.216  READ DMA
  c8 00 08 ca e8 2f f0 08      00:10:31.200  READ DMA
  c8 00 10 ba af a5 f2 08      00:10:31.184  READ DMA
  c8 00 08 aa ee 9d f2 08      00:10:31.184  READ DMA
  c8 00 18 5a 8d a2 f2 08      00:10:31.168  READ DMA

Error 98 occurred at disk power-on lifetime: 4052 hours (168 days + 20 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 04 9a 7c 35 f0  Error: UNC 4 sectors at LBA = 0x00357c9a = 3505306

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 9a 7c 35 f0 08      00:05:04.512  READ DMA
  c8 00 08 82 e8 a1 f2 08      00:05:04.496  READ DMA
  c8 00 08 9a 7c 35 f0 08      00:05:03.136  READ DMA
  c8 00 08 fa e7 a3 f2 08      00:05:03.120  READ DMA
  c8 00 08 9a 7c 35 f0 08      00:05:01.056  READ DMA

Error 97 occurred at disk power-on lifetime: 4052 hours (168 days + 20 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 04 9a 7c 35 f0  Error: UNC 4 sectors at LBA = 0x00357c9a = 3505306

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 9a 7c 35 f0 08      00:05:03.136  READ DMA
  c8 00 08 fa e7 a3 f2 08      00:05:03.120  READ DMA
  c8 00 08 9a 7c 35 f0 08      00:05:01.056  READ DMA
  c8 00 28 62 f6 de f1 08      00:05:01.040  READ DMA
  c8 00 08 9a 7c 35 f0 08      00:04:58.784  READ DMA

Error 96 occurred at disk power-on lifetime: 4052 hours (168 days + 20 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 04 9a 7c 35 f0  Error: UNC 4 sectors at LBA = 0x00357c9a = 3505306

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 9a 7c 35 f0 08      00:05:01.056  READ DMA
  c8 00 28 62 f6 de f1 08      00:05:01.040  READ DMA
  c8 00 08 9a 7c 35 f0 08      00:04:58.784  READ DMA
  c8 00 08 fa e7 35 f0 08      00:04:58.784  READ DMA
  c8 00 08 7a e9 9d f2 08      00:04:58.768  READ DMA
```

And...

```
root@dominus:/etc/default# smartctl -l selftest /dev/hdb
smartctl version 5.34 [i686-pc-linux-gnu] Copyright (C) 2002-5 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       40%      4054  3027954
# 2  Extended offline    Completed: read failure       40%      4054  3027954
# 3  Extended offline    Completed: read failure       40%      4054  3027954


```

---

### Post by LKRaider on 2006-06-18
I had a similar issue too. Even worse, the HD was making screeching noises upon boot (it was the primary disk), and I could not boot anymore from it.

I would suggest making a backup of whatever files are important on the disk, and then running the Maxtor Powermax utility to see if it can relocate the bad sectors on the disk.

That is what I did, and the tool said it successfully repaired my disk, and I didn't have any more problems yet (but it isn't my primary disk anymore, I then bought a 250Gb one ;)

---

### Post by musther on 2006-06-18
Thanks, I'll give that a go.  It is my primary disk, but it's got my root partition on it, home is on another, so whatever happens I'll not loose any data..

---

