---
title: "WD EARS, mdadm, and xfs - idle to sleep and load cycle problems"
date: 2010-12-13
forum: Hardware
---

### Post by shadowwyvernx on 2010-12-13
Hello,

I have a mdadm-driven RAID5 array with 4x WD20EARS drives (WD Green) on Ubuntu Server 10.10 (64 bit) on a SB700/SB800 controller in AHCI mode.  This array is strictly for storing data, and is at least not intended to be used for any significantly time-varying data (to be clear: I don't want it to be storing any such data).  The mount (/mnt/raid) is shared via samba.

As seems to be common, I am having load cycle count problems with the drives.  In addition to that, I am having trouble making the drives idle to sleep with hdparm - even after a whole night of no activity, the drives, which should have slept after 1 hour, were still awake.  I have seen them go to sleep once.

So, symptoms:
1) Drives will not idle to sleep using in rc.local 
```
hdparm -S242 /dev/disk/by-id/<id>
```
but, they will go to sleep and stay asleep with ```
hdparm -y <disk>
```
2) Load Cycle Count (SMART parameter Load_Cycle_Count) is increasing rather rapidly.  These Green drives are at around 4500, while the system drive (not a Green) is at 21 - they were installed at the same time, though the greens were disconnected from SATA for installation and perhaps a day of memory testing.

I will probably resort to the WD Idle utility other have used, but that does not solve my (1) symptom.  Additionally, something I have not heard addressed is the question of "Ok, so the heads park after 8 seconds of inactivity, a little low, granted, *but something has to wake them up again*" - the same "something" is probably preventing the drives from idling to sleep, but again, why do they stay asleep if I manually tell them to?  And if they stay asleep, why do the heads unpark so much?

What would be constantly touching a non-system drive?  The array is healthy, so mdadm should not be doing anything, no filesystem activity (and any writes should have been flushed overnight right?), so xfs should not be doing anything (I am even using the noatime mount option).  I did not leave any open Explorer windows on the Windows 7 client, so samba should not be doing anything. (note that these are notional conditions, I don't have any solid proof for example that there is no file system activity, I am simply not aware of any that should be occurring)

I understand that for logging purposes the system drive would need to be awake a lot, and at regular intervals.  But why a strictly data filesystem (that did not even exist when the system was installed)? Are there some tools that can help me identify the problem?

Here is lspci, if it helps:
```


00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 4)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] (rev 40)
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:15.0 PCI bridge: ATI Technologies Inc Device 43a0
00:15.1 PCI bridge: ATI Technologies Inc Device 43a1
00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4250]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
02:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ether                   net controller (rev 06)
04:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
05:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02)
05:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02)

```
Motherboard: Gigabyte 880GA-UD3H

Thanks very much :)

---

### Post by shadowwyvernx on 2010-12-13
I must issue an apology: My statement about there being no samba shares open was incorrect - I had the array (from a read only share) mapped to a network drive on the Windows 7 client.

I do want to report that after commenting out the hdparm commands in rc.local and power cycling the system (shutdown), I have noticed what I think is a reduction in the load cycle rate of increase.  Admittedly, I don't have a good baseline for the actual rate prior to this, but without issuing any hdparm commands, in 112 minutes, the load cycle count has only increased by 3 (worst of the drives).  That is 0.026 cycles/min, compared to an average of 0.58 cycles/min over the lifetime of the drive (128 hours)

---

### Post by shadowwyvernx on 2010-12-19
I believe I have narrowed down the problem.  After I loaded all of my data onto the array, I rebooted the system a few times for various configuration tweaks and such, and the result was that for several days the system sat in "steady state" - I would read data from the array periodically, and the disks would idle to sleep nicely.  However, yesterday I performed a write to the array (had some new files to add), note that during the steady state period above no writes were performed (and the file accessed from a read-only samba share).  The disks now no longer idle to sleep, even overnight.

Further investigation has confirmed writes (either from samba or locally using "cp") are the problem and unmounting and remounting the filesystem is the solution.  I do not have to stop the mdadm array, only unmount and remount the filesystem.

My quick browse through "man mount" did not give me any mount options that sounded like they would obviously fix my problem.  Are there any suggested options that will cause all writes to be fully committed (or any other activity that "umount" causes to occur) after some period of time?  I do care about write performance, and I'm fine with data sitting in memory for a little while until it is committed to the disk, but I would like to be able to set an upper bound to that period, after which there will be no filesystem activity.  Any suggestions?

Thanks again :)

---

