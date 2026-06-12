---
title: "Compatibility with 64-bit Ubuntu ?"
date: 2007-03-13
forum: Hardware &amp; Laptops
---

### Post by tjod on 2007-03-13
Hi;

Having been a reluctant Windows user for many years, Vista finally gave me the push I needed to get a machine  running only Linux - no dual boot, no weird partitions.  I have tried a few distros over the last few years and decided I like Ubuntu so that was my choice.  I installed 6.10 on a new Acer laptop and though there were some frustrating moments, (OK, days ...)  it's finally all running. Printers, video, wireless, wired network., most of my favorite apps or better replacements are now working . 

Well, now I'd like to do the same thing with a desktop machine.  It's currently running XP Pro x64 Edition. I'll probably wipe the C: drive and dedicate it to Ubuntu only. 

Here's the question(s):

Is there any kind of a compatibility list for Ubuntu where I can look up all the bits and pieces of the system and see if there are going to be any major challenges in terms of drivers, etc.?

Here's the system I'm thinking of using: 

Machine: STORMKING
System : ACPI Uniprocessor x64-based PC
CPU  : 1 x AMD Athlon(tm) 64 Processor 3200+ - 2050 MHz
Cache: 128 KB L1 + 512 KB L2 + 0 KB L3
Mainboard: ASUSTeK Computer Inc. A8V Deluxe
Memory   : 1023 MB
Operating system: Soon to be UBUNTU 64-bit 6.10, I hope
Display adapter: NVIDIA GeForce FX 5500
Video Memory         : 256 MB
Monitor: Samsung  SyncMaster 204b  
Fixed    : WDC WD2500JB-00GVC0 - 238472 MB (ATA)
C: (Primary NTFS - 238464 MB)
Fixed    : WDC WD1200JB-75CRA0 - 114439 MB (ATA)
D: (Primary NTFS - 114431 MB)
Z: DVD  : TSSTcorpCD/DVDW TS-H552B - 0 MB (ATAPI)
Removable drives A:
Audio: VIA AC'97 Enhanced Audio Controller
Network adapter: Marvell Yukon 88E8001/8003/8010 PCI Gigabit Ethernet Controller
Keyboard: Standard 101/102-Key or Microsoft Natural PS/2 Keyboard
Mouse: Microsoft PS/2 Mouse
Default printer: \\MAZAMA\HP8250

Thanks in advance for any ideas or pointers or warnings. 8-) 

Tim O

---

### Post by tgalati4 on 2007-03-13
Run a live CD (Dapper for stability, Edgy for cool stuff, Feisty if you feel lucky).  Then run dmesg and see what is happening during hardware detection.  You will see quite a few errors and warnings--for instance No SCSI devices found if you don't have any.  Post any strange errors on the forums--but search the forums first for these errors.  Most are common and can either be ignored or there are work arounds--as you have discovered with your laptop.

Good luck.  An Athlon 3200 should be a screamer under Ubuntu.

---

### Post by tjod on 2007-03-13
Thanks - I'll do that over the next week or so.

I think I'll go with Edgy since I would like to try Beryl or Compiz (sp?) Downloading the 64 bit torrent right now.

Tim O

---

### Post by tjod on 2007-03-13
Hmmmmmmm. 64-bit disk would not boot correctly.  Hash was ok though. Very odd. 

I went ahead and installed the 32-bit anyway. 

Need.
Seat.
Belt.
and. 
Roll. 
Bars.

Wooohaaaa!:)

---

