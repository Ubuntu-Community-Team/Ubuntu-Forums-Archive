---
title: "sata_nv is killing my drive"
date: 2007-12-09
forum: Hardware &amp; Laptops
---

### Post by coreSOLO on 2007-12-09
I am running Linux on my lappy with nvidia nforce 430 mobo and Seagate 120gb sata drive. The problem is that it gets exceptionally overheated and before you ask me to use laptop-mode-tools and disk spindown-things, please read the whole question as my problem is a little different.

So the problem is that my sata HDD gets very hot when running in Linux than when running in WindowsXP in both high IO and low IO works!

--------

First of all, I tested high IO mode this way :
- I tried it with coping a DVD image from one partition to another and watching a DAT file from disk itself so that I can stress it to max.
- After 3-5 minutes of work at max IO, temp reaches around 58-60 C. But if I try the same thing in windows, temp is 52-55 C max! This is 5 degree lower.

--------

Then I tested my disk in idle mode. First I configured power management options for my disk this way :
- set 5 seconds spin down with hdparm -S1
- tightest advanced power management setting using hdparm -B1
- acoustic setting was not supported for my drive so left it unchanged
- enabled laptop-mode-tools for lowering wakeups
- used hdparm -C to check the state
- when my disk spins up or down, I can hear it
- used smartctl and hddtemp to check temp in Linux
- used SpeedFan and MBM to check temperature in widows
- Apart from this, I can also touch my lappy and feel the diference

Okey so I left my lappy and made sure that there is absolutely no disk access for 2 mins. In windows, temp stays ok near 45-50 C but in Linux, it keep increasing upto 55-57 C. And please note that there was no disk access at all and the disk was in "standby" mode all the time.

-------

My system specs :

- compaq presario v3424au
- geforce go 6150 nforce 430
- segate sata 120 gb

- 64 bit kernel 2.6.22.12-0.1-default
- sata_nv version 3.4
- udma5 mode active

- WindowsXP SP2 32 bit
- Nvidia SATA drivers
- some SATA 1.5 G mode

-------

The help I seek :

1. Please tell me is there some known issues with sata_nv 3.4?
2. Is there any alternative to sata_nv?
3. Is there any possibility that by decreasing DMA or PIO mode (or any other hdparm/sdparm setting), I can reduce the stress on my disk?

A solution that decreases my disk performance will be acceptable if it solves my overheating issue, and once again, I would like to stress the difference in WinXP and Linux temps here. Any help would be appreciated.

---

### Post by coreSOLO on 2007-12-10
someone plz help, I've already given as much info as possible :(

---

