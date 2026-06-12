---
title: "Possible hardrive failure?"
date: 2013-12-14
forum: Hardware
---

### Post by Jacob72 on 2013-12-14
Running Xubuntu 13.04

I tried to boot and got this:

"ubuntu unt: /sys on /root/sys failed: mounting no such file or dir"

I booted on to another dirve and ran GSmartControl. I ran a short test and it stopped while running, here is the error log:

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

Error 11 occurred at disk power-on lifetime: 1628 hours (67 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 06 1a f2 37 ec  Error: UNC 6 sectors at LBA = 0x0c37f21a = 204993050

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 06 1a f2 37 ec 08      00:14:54.665  READ DMA
  c8 00 40 d8 f2 37 ec 08      00:14:54.664  READ DMA
  c8 00 48 68 f2 37 ec 08      00:14:54.664  READ DMA
  c8 00 18 28 f2 37 ec 08      00:14:54.657  READ DMA
  c8 00 10 f0 f1 37 ec 08      00:14:54.657  READ DMA

Error 10 occurred at disk power-on lifetime: 1628 hours (67 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 20 1a f2 37 ec  Error: UNC 32 sectors at LBA = 0x0c37f21a = 204993050

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 20 08 f2 37 ec 08      00:14:52.575  READ DMA
  c8 00 08 00 f2 37 ec 08      00:14:52.574  READ DMA
  c8 00 20 d0 f1 37 ec 08      00:14:52.574  READ DMA
  c8 00 08 c8 f1 37 ec 08      00:14:52.574  READ DMA
  c8 00 20 58 f1 37 ec 08      00:14:52.574  READ DMA

Error 9 occurred at disk power-on lifetime: 1628 hours (67 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 f0 1a f2 37 ec  Error: UNC 240 sectors at LBA = 0x0c37f21a = 204993050

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 f0 18 f2 37 ec 08      00:13:40.071  READ DMA
  c8 00 08 10 f2 37 ec 08      00:13:40.070  READ DMA
  c8 00 08 08 f2 37 ec 08      00:13:40.070  READ DMA
  c8 00 f0 18 f1 37 ec 08      00:13:40.070  READ DMA
  c8 00 08 10 f1 37 ec 08      00:13:40.070  READ DMA

Error 8 occurred at disk power-on lifetime: 1628 hours (67 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 f0 1a f2 37 ec  Error: UNC 240 sectors at LBA = 0x0c37f21a = 204993050

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 f0 18 f2 37 ec 08      00:13:38.225  READ DMA
  c8 00 08 10 f2 37 ec 08      00:13:38.225  READ DMA
  c8 00 08 08 f2 37 ec 08      00:13:38.225  READ DMA
  c8 00 f0 18 f1 37 ec 08      00:13:38.224  READ DMA
  c8 00 08 10 f1 37 ec 08      00:13:38.224  READ DMA

Error 7 occurred at disk power-on lifetime: 1628 hours (67 days + 20 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 f0 1a f2 37 ec  Error: UNC 240 sectors at LBA = 0x0c37f21a = 204993050

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 f0 18 f2 37 ec 08      00:13:35.774  READ DMA
  c8 00 08 10 f2 37 ec 08      00:13:35.773  READ DMA
  c8 00 08 08 f2 37 ec 08      00:13:35.773  READ DMA
  c8 00 f0 18 f1 37 ec 08      00:13:35.773  READ DMA
  c8 00 08 10 f1 37 ec 08      00:13:35.773  READ DMA
```
I also ran a long test I stopped well short of 49min and said no errors?

I have heard the dreaded electronic clicking noise coming from my tower, which is the sound of a failing HD no?

Thanks

---

### Post by tgalati4 on 2013-12-14
Boot a LiveDVD or USB stick and see if you can even mount the drive.  Have a second drive or USB stick ready to capture data because you don't have much time for recovery.

---

### Post by Jacob72 on 2013-12-14
I ran Boot repair from the terminal using:

> sudo boot-repair && (boot-repair &)

I was able to boot on the drive but I am getting page freezes seems to be mostly when browsing? What test can I do, do you think I need more RAM?

---

### Post by tgalati4 on 2013-12-14
Have you backed up or recovered any critical data on this drive?  If not, then do so now.  Otherwise, burn a copy of UBCD and use the manufacturer's tool to run a diagnostic and perform a low-level format.  If it fails the low-level format, then you know the drive is bad.

The page freezes are most likely happening because the browser cache is slow to fill the pages because of correctable and uncorrectable (UNC) errors--just as SMART has reported.  More RAM will help if you set up firefox or chrome to run completely from RAM (i.e. use a RAMdisk instead of the hard disk to store the cache profile).

---

### Post by Jacob72 on 2013-12-15
"perform a low-level format"

I ended up totally formating the hard drive after backing up my data. Will that give any clue as to the state of the HD?

Now I am unable to run off my bootable USB. The boot gets as far as the XUbuntu splash screen but hangs there with no language options etc.. I am now running an old install on another drive in the same computer, is there system checks I can do? 

Should I start a new post?

---

### Post by Andrew_Lucas on 2013-12-15
Annoying as it is - I wouldn't panic about USB flash hanging. I reformat all the time and it seems to happen fairly regularly. Usually a formatting the stick and putting a fresh .iso on works - occasionally have to mess with BIOS settings (e.g. turning UEFI on/off, making sure I've created a USB for a UEFI install on a UEFI computer).
Given the other problems you're having with the hard drive, though, it might be indicative of something else. There's probably the equivalent of Memtest for hard drives, maybe try Googling 'hard drive stress test'? If it fails...that would be very suggestive. Obviously, make sure any valuable data is backed up first.

Good luck!

---

### Post by tgalati4 on 2013-12-15
*phoronix-test-suite* is about as extensive as they come.  Dell, HP and others have diagnostic utilities that you can download and burn to CD and run tests from a Live CD DOS session.  There may be some on UBCD that you can use as well.  Hard disk tests can be done through SMART and using *badblocks*.  The manufacturer's tools (on UBCD) also have diagnostics that you can run.

---

### Post by Jacob72 on 2013-12-15
@t Thanks for the list, One thing about diagnostics software is I never understand the report ... I suppose I can post it. I removed the suspect HD and all running smooth again. The worrying thing is that this is the second HD that has become faulty not more than a year after buying them new. This time I may have had the partitions set incorrectly?

---

### Post by tgalati4 on 2013-12-15
Bad cables or weak power supply or motherboard chipset that is failing--it could be a lot of things.  If both drives were the same model, it could be a bad batch of drives.  I've never seen a partition error that would cause the problems that you are seeing.  The kernel can either read the partition correctly and you have enough space to install and run, or errors will get thrown up showing that you have partition errors that need fixing using fdisk or gparted.  If you run out of space, then you will get errors to that effect as well.

If your hardware is not perfect, you will get a bunch of strange errors that will never really pinpoint the exact issue.  Intermittent problems can be the most difficult to troubleshoot.

New disk drives do need a certain about of break-in time.  This weeds out early failures (called Infant Mortality).  Once the drives have some hours on them, then you can install the operating system and you should be all set for several years.

What is the make and model of these drives?  A simple google search will show if others are having problems with these drives.

---

