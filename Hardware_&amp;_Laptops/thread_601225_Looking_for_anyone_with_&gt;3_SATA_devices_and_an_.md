---
title: "Looking for anyone with &gt;3 SATA devices and an Intel-chipset motherboard that works"
date: 2007-11-03
forum: Hardware &amp; Laptops
---

### Post by tlunde on 2007-11-03
Do you have a box that has 4 or more SATA devices attached to an Intel chipset motherboard and which is working without problems?  I'd love to hear from you.  

It can be any Intel-based box:  P35, P965, P945 with add-in cards, whatever.  If you have 3 SATA devices and one IDE device, then that won't help.

I suspect a kernel problem and am trying to gather evidence to either confirm or contradict that theory.  Even a short "works for me" and a short description of your working config would be appreciated.



I have a box that has a GIGABYTE GA-P35-DS3R motherboard.  The Intel P35 chipset has an ICH-9 SATA controller according to Wikipedia:
[http://en.wikipedia.org/wiki/List_of_Intel_chipsets](http://en.wikipedia.org/wiki/List_of_Intel_chipsets) (search for P35)

It worked fine from August until last week.  During most of that time it had 3 SATA hard drives; it started life with just one SATA drive.  It also has a CD-RW/DVD-ROM IDE device, 4G of RAM and a quad-core processor.  

Last week, I added in a fourth SATA hard drive.  The system booted fine and then (for the first time since the build) started having problems.  I've tried lots of changes and when I have 4 STA devices, I always have problems.  With <4 SATA devices, they all go away.  The problems vary, but all amount to the system dying within a short time (2 min to 3 hours) of a reboot.  

When the box dies, it does not have a hard crash.  Rather it starts logging SATA errors.  I've now seen them against all drives, but I saw them first on the oldest device in the box (and the most active), the root device.  The errors look similar to this one:

Oct 28 18:37:54 entrepot -- MARK --
Oct 28 18:39:51 entrepot kernel: [12121.083648]          res 61/04:01:e0:2f:f6/0
4:00:1e:00:00/f0 Emask 0x1 (device error)
Oct 28 18:39:51 entrepot kernel: [12121.090973] ata6.01: ata_hpa_resize 1: secto
rs = 976773168, hpa_sectors = 0
Oct 28 18:39:51 entrepot kernel: [12121.137000] ata6.00: ata_hpa_resize 1: secto
rs = 976773168, hpa_sectors = 976773168
Oct 28 18:39:51 entrepot kernel: [12121.137005] ata6.00: configured for UDMA/133
Oct 28 18:39:51 entrepot kernel: [12121.137213] ata6: failed to recover some dev
ices, retrying in 5 secs
Oct 28 18:39:56 entrepot kernel: [12126.134647] ata6: soft resetting port
Oct 28 18:39:56 entrepot kernel: [12126.298789] ata6.01: ata_hpa_resize 1: secto
rs = 976773168, hpa_sectors = 0
Oct 28 18:39:56 entrepot kernel: [12126.334800] ata6.00: ata_hpa_resize 1: secto
rs = 976773168, hpa_sectors = 976773168
Oct 28 18:39:56 entrepot kernel: [12126.401331] ata6.00: ata_hpa_resize 1: secto
rs = 976773168, hpa_sectors = 976773168
Oct 28 18:39:56 entrepot kernel: [12126.401337] ata6.00: configured for UDMA/133
Oct 28 18:39:56 entrepot kernel: [12126.401541] ata6.01: limiting speed to UDMA/
133:PIO3
Oct 28 18:39:56 entrepot kernel: [12126.401544] ata6: failed to recover some dev
ices, retrying in 5 secs
Oct 28 18:40:01 entrepot kernel: [12131.398356] ata6: soft resetting port
Oct 28 18:40:01 entrepot kernel: [12131.562463] ata6.01: ata_hpa_resize 1: secto
rs = 976773168, hpa_sectors = 0
Oct 28 18:40:01 entrepot kernel: [12131.599151] ata6.00: ata_hpa_resize 1: secto
rs = 976773168, hpa_sectors = 976773168
Oct 28 18:40:01 entrepot kernel: [12131.657368] ata6.00: ata_hpa_resize 1: secto
rs = 976773168, hpa_sectors = 976773168
Oct 28 18:40:01 entrepot kernel: [12131.657374] ata6.00: configured for UDMA/133
Oct 28 18:40:01 entrepot kernel: [12131.657596] ata6.01: disabled
Oct 28 18:40:01 entrepot kernel: [12131.657599] ata6: failed to recover some dev
ices, retrying in 5 secs

etc etc

When this happens to the root device, the system stays "up" but (usually) no more process can be launched.  Thus, a hard reset/power-off is the only way out.

In the last few days, I've tried:
--unplugging and testing individual devices.  With less than three active SATA drives, the system is fine.  smartmontools doesn't seem to find any problems.
-- booting from CD and running a 14 hour RAM test.  No problems found.
-- booting from a different SATA drive.  (I'd had a backup / partition on what had been sdc.)

The system still runs an up-to-date feisty (or, well, up to date when the problems started.)

Googling has been little help.  The closest thing that I've found is:
[http://lkml.org/lkml/2007/8/30/123](http://lkml.org/lkml/2007/8/30/123)

I checked in with Jerome yesterday.  He still has the problem.  Looking around ubuntuforums, I see a very small set of posts that seem to indicate >3 sata devices (usually three hard drives and a SATA optical device) and various problems (can't boot, random freezes, etc.) but none where I can identify >3 SATA devices working on an Intel-based motherboard.

Whether you've got a working config or you think you've experienced this problem, I'd appreciate hearing from you if you have this combination of hardware.  

If you've got any suggestions for further troubleshooting steps, I'd appreciate it.

Thanks!


tlunde@entrepot:/var/log$ lspci
00:00.0 Host bridge: Intel Corporation Unknown device 29c0 (rev 02)
00:1a.0 USB Controller: Intel Corporation Unknown device 2937 (rev 02)
00:1a.1 USB Controller: Intel Corporation Unknown device 2938 (rev 02)
00:1a.2 USB Controller: Intel Corporation Unknown device 2939 (rev 02)
00:1a.7 USB Controller: Intel Corporation Unknown device 293c (rev 02)
00:1b.0 Audio device: Intel Corporation Unknown device 293e (rev 02)
00:1c.0 PCI bridge: Intel Corporation Unknown device 2940 (rev 02)
00:1c.3 PCI bridge: Intel Corporation Unknown device 2946 (rev 02)
00:1c.4 PCI bridge: Intel Corporation Unknown device 2948 (rev 02)
00:1d.0 USB Controller: Intel Corporation Unknown device 2934 (rev 02)
00:1d.1 USB Controller: Intel Corporation Unknown device 2935 (rev 02)
00:1d.2 USB Controller: Intel Corporation Unknown device 2936 (rev 02)
00:1d.7 USB Controller: Intel Corporation Unknown device 293a (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation Unknown device 2916 (rev 02)
00:1f.2 IDE interface: Intel Corporation Unknown device 2920 (rev 02)
00:1f.3 SMBus: Intel Corporation Unknown device 2930 (rev 02)
00:1f.5 IDE interface: Intel Corporation Unknown device 2926 (rev 02)
02:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
02:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
04:00.0 VGA compatible controller: Trident Microsystems TGUI 9660/938x/968x (rev d3)
04:01.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
tlunde@entrepot:/var/log$

---

### Post by netbandit on 2007-11-04
I've lost close to 1TB woth of drives over the last 6 months... and hate to say that it could well be your drive is going bad?

You can get diagnostic discs/ISO's from most manufacturers.  If your manufacturer does not have one, the IBM/Hitachi Drive fitness test disk should work.

I hope that you dont have a bad drive, but I also hope you aren't having mystery problems either.

Good luck!
-nb

---

### Post by jeepescu on 2008-01-17
I am running 3 SATA discs and one DVD+RW on a Gigabyte P35 DS3R with no problems (except sound and power management).
Let me know if I can help you in any way.
Forgot to mention, even at one point I was running 4 HDs ( 1xraptor, 1xWD250 and 2xSEagate 320) + the DVD-RW without any problems. 
Controller could be in IDE or AHCI, all was OK, unlike windows :( :( :(  
I have been running Feisty, and since about two weeks, Gutsy.
HTH

---

