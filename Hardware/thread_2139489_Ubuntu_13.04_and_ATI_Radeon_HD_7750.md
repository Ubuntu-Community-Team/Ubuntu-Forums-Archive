---
title: "Ubuntu 13.04 and ATI Radeon HD 7750"
date: 2013-04-27
forum: Hardware
---

### Post by tycoon35 on 2013-04-27
Do Ubuntu 13.04 support ATI Radeon 7750 Graphics Card?

The last Catalyst driver release for linux with 77xx series support states that it is compatible with 12.10 (released on 24.04.2013)

[http://support.amd.com/us/kbarticles/Pages/AMDCatalyst13-4LINReleaseNotes.aspx](http://support.amd.com/us/kbarticles/Pages/AMDCatalyst13-4LINReleaseNotes.aspx)

I am going to buy the graphics card before finally setting up my desktop with new SSD(64gb)+ new 1.5tb HDD+ new GPU and top of all new OS i.e. Ubuntu(moving from Windows completely). So I need to know the obstacles I may be facing.

As some other topic about 7750 GPU stated, someone could manage to make it work by downgrading the OS and then upgrading while keeping the older drivers! Can that be an option?

Btw, some people seems to be anxious to mention how Nvidia supports are better for Linux in the forum. But I find the benchmark and prices are much more user friendly with ATI cards.

---

### Post by tycoon35 on 2013-07-11
Well I am a little late to mention, but I have installed Ubuntu 13.04 with AMD drivers for HD Radeon 7750 successfully. Now by successful I mean that every info checking out fine with my GPU version and drivers. But in the process I was forced to install my Windows OS back too! The reason was the Video play(& not games)! My videos in Ubuntu was getting too many blurs :/ Even the 720p(MKV format music video) ones not running properly in VLC or, any MPlayer derivatives. Same ones running pretty smooth in Windows(even with Windows Media Player!).

So in the end I failed to make Ubuntu my default OS at least for now once again! I would really like if anyone could share some insight about the issue and help me fix it if at all possible now or in near future.

Thanks.

In case if it helps here is my system configuration from Windows machine.

> Mainboard :    Gigabyte GA-880GM-USB3
Chipset :    AMD 880G
Processor :    AMD Phenom II X4 955e @ 3200 MHz
Physical Memory :    8192  MB (2 x 4096 DDR3-SDRAM )
Video Card :    AMD Radeon HD 7700 Series(**7750**)
Hard Disk :    KINGSTON SV100S264G ATA Device (64GB)
Hard Disk :    Western Digital WD20EZRX-00DC0B0 ATA Device (2000GB)
DVD-Rom Drive :    HL-DT-ST DVDRAM GH22NS50
CD-Rom Drive :    DTSOFT Virtual CdRom Device
Monitor Type :    Samsung SMB2230 - 22 inches
Network Card :    Realtek Semiconductor RTL8168/8111 PCIe Gigabit Ethernet Adapter
Operating System :    Windows 7 Ultimate Professional Media Center 6.01.7601 Service Pack 1 (64-bit)
DirectX :    Version 11.00
Windows Performance Index :    6.8 on 7.9

---

### Post by Yellow Pasque on 2013-07-11
If you're running the proprietary AMD fglrx/Catlayst driver, the best video player option is XBMC using xvba output: [https://launchpad.net/~wsnipex/+archive/xbmc-xvba-frodo](https://launchpad.net/~wsnipex/+archive/xbmc-xvba-frodo)

---

### Post by 00b00nt00 on 2013-07-13
I gave up on using Ubuntu on AMD systems. I have a laptop with a crappy Pentium b950 with integrated Intel graphics and a Phenom II x6 tower with Radeon 7750 and the Pentium tears strips off the x6/7750 using Ubuntu.

---

### Post by AKmTc6r on 2013-09-05
Greets forum. Have not tried the intel path... ( amd fanboy [IMG]http://ubuntuforums.org/images/icons/icon14.png[/IMG] ). But im currently using a athlon II x2 270 with 5450 512mb ddr3... Asus m4a785g htpc with ubuntu 13.04, its swallowing 15-20gb mkv test files. So your x6 phenom II is not the problem, its driver related when using 7750..[IMG]http://ubuntuforums.org/images/icons/icon9.png[/IMG] I just bought a 7750 1gb ddr5 from xfx, and desktop is now so sluggish, i cant use it for anything (Note self: dont buy bleeding egde effeciency and if its not broken, dont fix it). If you try older cards, im guessing you will experience hassle-free video viewing. Sry if off-topic a little, have a nice day all :-D

---

