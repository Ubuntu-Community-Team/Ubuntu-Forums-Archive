---
title: "Realtek 880 Audio Driver?"
date: 2006-12-10
forum: Hardware &amp; Laptops
---

### Post by Tokamak7700 on 2006-12-10
I have looked through endless How-to guides and Help documents on installing audio hardware.  None of which are working for me for one reason or another.  I am new to Linux so I will try my best to describe my problem.

I have the Realtek 880 audio chipset for my Alienware 7700 laptop.  Other 7700 users say that the audio automatically works after installing Ubuntu, but I can not get it working.

I receive this error message when trying to "Test" the audio when in the System => Preferences => Sound.
> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not negotiate format

This is my Hardware:
> 00:00.0 Host bridge: Intel Corporation 915G/P/GV/GL/PL/910GL Express Memory Controller Hub (rev 0e)
00:01.0 PCI bridge: Intel Corporation 915G/P/GV/GL/PL/910GL Express PCI Express Root Port (rev 0e)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 05)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 05)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 05)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 05)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 05)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d5)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 05)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0299 (rev a1)
0a:00.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
0a:01.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
0a:02.0 RAID bus controller: Promise Technology, Inc. PDC20378 (FastTrak 378/SATA 378 ) (rev 02)
0a:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
0b:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 2a02 (rev 03)

Thanks for any help you can give me.  If you need more info, please let me know.  Also, please try to keep it simple, I'm still getting used to Linux & the command line...     ](*,)

---

### Post by Tokamak7700 on 2006-12-10
Bump...

---

### Post by sddfdds on 2007-01-15
I have the same laptop, and unfortunately, was never able to find a solution to this problem.

---

