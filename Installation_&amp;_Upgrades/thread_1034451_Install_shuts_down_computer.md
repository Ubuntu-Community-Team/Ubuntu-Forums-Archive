---
title: "Install shuts down computer"
date: 2009-01-08
forum: Installation &amp; Upgrades
---

### Post by clayrab on 2009-01-08
Hello all,
I'm trying to install Ubuntu for the first time but every time I try to install it my box suddenly powers down.  It happens near the beginning of the install when the progress bar is filling and is about 75% complete.  I have tried multiple CDs(kubuntu 64, ubuntu 64, and kubuntu i386) and have tried multiple harddrives.  I don't have an extra DVD/CD drive to try.  I doubt that it is a power problem because I have a 550W PSU and have tried disconnecting my extra HDs just in case this was the issue.  I might try installing from USB key when my roommate gets home but I'm not sure if he has one.  Does anyone have any idea what could be causing this?
Thanks!
-Clay

---

### Post by oldos2er on 2009-01-08
Please post your hardware specs.

---

### Post by clayrab on 2009-01-08
Windows: Windows XP5.1 (Build 2600) Service Pack 3
Internet Explorer: 7.0.5730.13
Memory (RAM): 2048 MB
CPU Info: Mobile AMD Athlon(tm) 64 Processor 3400+
CPU Speed: 803.4 MHz
Sound card: Mia 1-2 Virtual Out
Display Adapters: NVIDIA GeForce 6800 Series GPU | LogMeIn Mirror Driver | NVIDIA GeForce 6800 Series GPU | NetMeeting driver | RDPDD Chained DD
Monitors: 2
Screen Resolution: 1680 X 1050 - 32 bit
Network: Network Present
Network Adapters: NVIDIA nForce Networking Controller - Deterministic Network Enhancer Miniport
CD / DVD Drives: D: _NEC    DVD_RW ND-3520A  | E: FC1752C JIR104W          | F: FC1752C JIR104W
COM Ports: COM1
LPT Ports: LPT1
Mouse: 8 Button Wheel Mouse Present
Hard Disks: C:  69.2GB | G:  74.5GB | H:  372.6GB
Hard Disks - Free: C:  52.7GB | G:  71.2GB | H:  39.1GB
USB Controllers: 2 host controllers.
Firewire (1394): Not Detected
PCMCIA (Laptops): Not Installed
Manufacturer: Phoenix Technologies, LTD
Product Make:  
AC Power Status: OnLine
BIOS Info: AT/AT COMPATIBLE | 07/01/05 | Nvidia - 42302e31
Time Zone: Eastern Standard Time
Battery: No Battery
Motherboard: [http://www.abit.com.tw/](http://www.abit.com.tw/) NV8(NF-CK804)
Modem: Not detected

---

### Post by clayrab on 2009-01-09
It is either my DVD drive, my motherboard, my video card, or my PSU...  Is there any way to debug this!?

---

### Post by oldos2er on 2009-01-09
Did you run 'Check CD for defects' from the first menu?

---

### Post by Kevbert on 2009-01-09
Have you run memtest from the CD menu ? It's probably worth running it for two or three passes (Windows may just give you an occassional random crash).
At a guest I'd suggest it's probably the motherboard as other people on the forum have Nvidia 6800 cards and haven't reported any problems with installation.  If it was the CD drive you would probably get a crash quite early on. I'm assuming the failure occurs at the same point (approx 75% of the install completed).
You could try booting with different command line parameters such as turning off ACPI, see [[COLOR="Red"]here[/COLOR]]("https://help.ubuntu.com/community/BootOptions").

---

