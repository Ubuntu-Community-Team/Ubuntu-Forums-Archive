---
title: "Install Problems with Supermicro 5014C-MT server"
date: 2005-04-06
forum: Hardware &amp; Laptops
---

### Post by clientserver on 2005-04-06
I have a brand new Supermicro 5014C-MT server which is fairly new hardware (probably part of the problem is some things may be too new to be well supported):
Server details:
[http://www.supermicro.com/products/system/1U/5014/SYS-5014C-MT.cfm](http://www.supermicro.com/products/system/1U/5014/SYS-5014C-MT.cfm)
Motherboard details:
[http://www.supermicro.com/products/motherboard/P4/E7221/P8SCT.cfm](http://www.supermicro.com/products/motherboard/P4/E7221/P8SCT.cfm)

Basically it has the Intel E7221 server chipset with ICH6R SouthBridge (which has integrated LSI SATA RAID).

First it appears that the Hoary RC (64bit) installer would not detect the CD, which is a problem that has also happened to others in the past, see the following bug and the bug that is referred to therein:
[Bug 8602](https://bugzilla.ubuntu.com/show_bug.cgi?id=8602)

I took a real pita solution which was to create a linux partition on an external usb harddrive, copy the contents of the install CD to it, and then to boot off the install CD, mount the external usb drive as /cdrom, and proceed with next steps of the 'server-expert' install (actually I also had to overcome an odd problem where it could not find the file "/cdrom/dists//Release", which I fixed by moving the dists dir and creating symlinks so that dists/hoary was actually in dists, and some additional links so that the 'correct' paths still worked).

I was able to get the installer components to load, and there was no trouble detecting and configuring the gigabit ethernet, but when it came to the partitioning step, the only harddrive listed was the external usb one ... there was no option to use my RAID1 set (already previously configured and initialized and detected by the Intel ICHR6/LSI BIOS).   Based on the dmesg output and a scan of /dev, it looks like the RAID1 set is not being detected.   Anyone have any suggestions?

This server is officially supported/supposed to work (including the SATA RAID, etc) with RHEL 3+ or SUSE 9+, so although I would very much love to get Ubuntu to work, if that simply isn't possible then I will have to give one of those a try.

---

### Post by clientserver on 2005-04-07
I tested practically every combination of SATA-related BIOS settings and documented the resulting behavior that I see from the Hoary install CDs (I tested both the RC and 2005-04-04 snapshots which behaved identical). 
These settings are all in the main system BIOS (Phoenix - AwardBIOS v6.00PG ; motherboard is Supermicro P8SCT BIOS Rev 1.0A - which is the latest), under Advanced -> Advanced Chipset Control -> *** On-Chip Serial ATA Setting ***:

SATA Mode: RAID
On-Chip Serial ATA: Enhanced Mode
=Hoary result: No CD, No Hard Drives detected; segfault

SATA Mode: AHCI
On-Chip Serial ATA: Enhanced Mode
=Hoary result: No CD, No Hard Drives detected; segfault

SATA Mode: IDE
On-Chip Serial ATA: Enhanced Mode
=Hoary result: CD and All Hard Drives detected OK; segfault

SATA Mode: IDE
On-Chip Serial ATA: Auto
=Hoary result: CD and All Hard Drives detected OK; segfault

SATA Mode: IDE
On-Chip Serial ATA: Combined Mode
=Hoary result: CD and One Hard Drive detected*; NO segfault!

SATA Mode: IDE
On-Chip Serial ATA: SATA Only
=Hoary result: Cannot even boot from CD

SATA Mode: IDE
On-Chip Serial ATA: Disabled
=Hoary result: CD but No Hard Drives detected; segfault

*Note that in IDE-Combined Mode, there is a limit on the number of channels, so a second hard drive is not detected because it is on a channel that is no longer available to the BIOS in that mode -- this is not an Ubuntu issue (with that setting the BIOS doesn't see the second HD either).
Why IDE-Combined Mode is the only mode that does not result in a kernel segfault is beyond me.

Based on what I have read (concerning performance and such of BIOS-supported software RAID vs Linux software RAID), I have decided to abandon trying the RAID-Enhanced Mode anyway (incidentally that is the only setting in which the integrated Intel ICH6R / LSI RAID BIOS is active).
I would however very much like to use the AHCI-Enhanced Mode setting (along with Linux software RAID1) so that I can take advantage of the Native Command Queueing and hotplug features (although that may require a newer 2.6 kernel - [http://linux.yyz.us/sata/sata-status.html](http://linux.yyz.us/sata/sata-status.html) ).

Does anyone have any suggestions?
Should it be possible to install the system in IDE-Enhanced Mode for now, and then switch to AHCI-Enhanced Mode later once the issue is fixed (without having to reinstall)?

---

### Post by clientserver on 2005-04-08
Just a quick note, I also tested the latest version of the Sid-AMD64 installer
and it also has problems with AHCI (I used
[http://debian-amd64.alioth.debian.org/install-images/sid-amd64-monolithic.iso](http://debian-amd64.alioth.debian.org/install-images/sid-amd64-monolithic.iso)
dated 2005-04-05).
I also tested Overclockix 3.8 (basically Knoppix 3.8 CeBit edition, kernel
2.6.11 SMP i686) and AHCI mode seems to work fine there (with no segfaults either).

---

