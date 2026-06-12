---
title: "nVidia GeForce FX5500 agp8x"
date: 2007-11-08
forum: Hardware &amp; Laptops
---

### Post by Hdx on 2007-11-08
I'm having trouble installing my nVidia GeForce fx5500 agp8x256mb tv-out dvi
PIN: NA-55000+TD21-FM8336
S/N: NA-55000+TD21VN05025777

I have Gibbon installed.
Every time I boot with the card in the AGP slot, the system errors after the 'Loading Device Drivers' line.
Suggestions?
~Hdx

---

### Post by taurus on 2007-11-08
Do you have an onboard video card?

---

### Post by Linicks on 2007-11-08
> **Hdx said:**
> I'm having trouble installing my nVidia GeForce fx5500 agp8x256mb tv-out dvi
PIN: NA-55000+TD21-FM8336
S/N: NA-55000+TD21VN05025777

I have Gibbon installed.
Every time I boot with the card in the AGP slot, the system errors after the 'Loading Device Drivers' line.
Suggestions?
~Hdx

If you have an option in BIOS, drop the rate to AGPx2 (or perhaps AGPx4 if x2 is not available) and try that.

Read my old report here on the nVidia forums:

[http://www.nvnews.net/vbulletin/showthread.php?t=69877&highlight=agpx2](http://www.nvnews.net/vbulletin/showthread.php?t=69877&highlight=agpx2)

Nick
P.S. You will not see any difference between x2/x4/x8 AGP anyway, so run at the lowest stable setting.

---

### Post by Hdx on 2007-11-08
Yes I have an onboard vid adaptor, thats how I'm running the box now.
But its crap, its got like 2mb vram to it. And shairs the CPU
As for my Bios:
Phoenix - AwardBIOS CMOS Setup Utility

Standard CMOS Features
---Date (mm:dd:yy) Thu, Nov 8 2007
---Time (hh:mm:ss) 21:45:5
---IDE Primary Master [Maxtor 6L160P0]
---IDE Primary Slave [None]
---IDE Secondary Master [LG CD-RW CED-8120B]
---Drive A [None]
---Floppy 3 Mode Support [Disabled]
---Video [EGA/VGA]
------CGA 40
------CGA 80
------MONO
---Halt On [All Errors]
------No errors
------All, But Keyboard
------All, But Diskette
------All, But Disk/Key
---Base Memory 640K
---Extended Memory 785408K
---Total Memory 786432K

Thats all I could find for Video
~Hdx

---

### Post by Linicks on 2007-11-08
Have a look under 'Advanced Chipset features', if you have that.

Nick

---

### Post by Hdx on 2007-11-08
DRAM Timing Selectable [By SPD]
---Manual
CAS Latency Time 2.5
Active to Precharge Delay 7
DRAM RAS# to CAS# Delay 3
DRAM RAS# PreCharge 3
Command Pre Clock [Auto]
---Optimal
Memory Frequency For [Auto]
---DDR266
---DDR333
System BIOS Cacheable [Disabled]
---Enabled
Video BIOS Cacheable [Disabled]
---Enabled
Delayed Transaction [Enabled]
---Disabled
AGP Apreture Size (MB) [128]
---4
---8
---16
---32
---64
---256
**On-Chip VGA Settings***
On-Chip Video Windows Size [128MB]
---64MB
---Disabled
On-Chip Frame Buffer Size [8MB]
---1MB
~Hdx

---

### Post by xyphur on 2007-11-08
Read your motherboard manual. Find where it details disabling the on-board video adapter in the CMOS Setup Utility (BIOS, whtvr). This should fix your problem.

For future reference, knowing the ins and outs of your computer's BIOS is essential to troubleshooting hardware faults. Most times, it's an incorrect setting that just needs a little tweaking.

Best of luck.

EDIT: It isn't very common, but you may actually have to change a jumper setting on the motherboard itself to disable the on-board video... in which case, there wouldn't be anything in the BIOS except for the window size , AGP Aperture size,  and Framebuffer Size - all of which just tell the machine how much physical RAM to share with the video subsystem in different ways.

---

### Post by Hdx on 2007-11-08
I think, that with my MB the onboard is disabled by inserting an AGP card. As when I move the plug fromt he card to the onboard, it gets no signal.
~Hdx

---

