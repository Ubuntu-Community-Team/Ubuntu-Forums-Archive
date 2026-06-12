---
title: "Determining best parts from old spare pcs"
date: 2007-04-29
forum: Hardware &amp; Laptops
---

### Post by aleska on 2007-04-29
I have two older pcs, both Pentium 4s I believe, that are gathering dust in my basement.  I found neither to be really good enough / fast enough / whatever to run Ubuntu.  Tried xfce on one, but it tended to hang.  Anyway, I was thinking maybe I should turn one of them into a firewall, or turn em into a home server of some sort.  
Anyway, here's the question, is there a reasonable way to gauge which one is more solid than the other?  I'm pretty clueless about hardware.  What should I be comparing / contrasting?  Also what commands would I run in bash on each to provide a good, layman interpretable, run down of what the pc has got in it and what the relevant specs are?  I guess I'd prefer to know that I'm taking the best pieces from both (if one sound card is better than the other, or one video card, etc. etc.).
Thoughts and help - greatly appreciated!

---

### Post by aleska on 2007-04-29
just realized I posted this in Community Cafe, not in a general help section.  Moderator - please move to an appropriate forum if Community Cafe is an inappropriate place for this.
Thanks and sorry.

---

### Post by K.Mandla on 2007-04-29
I'll drop this into Hardware for you. ;)

When you say they're too slow for Ubuntu, how old a computer are you talking about? Pentium 4 should be plenty fast. Do you mean a plain old Pentium? 

Try ```
lspci -vvv
```for an idea of what the guts are.

---

### Post by Compucore on 2007-04-29
How fast are your two older Piv's there? I mean they should be able to handle Ubuntu without a problem. I've been using Ubuntu from a socket 7 processor running an AMD K6-2-450 without a hitch which is considered slow to todays PIV's. If they and my latest laptop is a PIV as well running at 1.60 ghz which is fast enough doe me to do what I need to work with over here. Do you remember the specs on the older machines?  Just go into the bios and take note of the speed, memory and hard drive space. You can do a lot of things with the older computers. Even to convert them to serve mp3 or your favorite movie files that are on the hard drive of the server. 

COmpucore

---

### Post by DeadToad on 2007-04-29
Compucore, Man! are we on the same page!  I am running Ubuntu Feisty Fawn v7.04 on an old Super Socket7 mobo with an AMD K6-2/450MHz CPU with 384MB PC100 SDRAM.
It's kinds slow, sluggish, have to reboot several times (most times) to get it running.  Sometimes when I boot, the mouse locks up.  So I reboot, then fine.  Other times, it locks up booting up.  Rarely does it boot normally.
My old Yamaha YMF719 OPL3-SAx 16-bit ISA Soundcard is not detected, and does not work.  Everything else is good.  I've given up on it.
I have the tower for sale for $100 + Shipping.
Windows 98SE is on drive C:\
Linux Ubuntu Feisty Fawn v7.04 is on drive D:\

Here's the specs:
MOTHERBOARD: #SPS-MBM-S71   Board: MVP3-586B-W83877TF
VisionTop/Xcesstech S7-MVP3 Super Socket7, 64-bit ATX, 2X/AGP Port, 100MHz FSB, 1MB Pipelined Burst SRAM Cache
Chipset: VIA Apollo MVP3 66/75/100MHz Front Side Bus Chipset.
Chipset VT82C598AT system controller (476 pin BGA) & VT82C586B PCI to ISA bridge (208 pin PQFP)
BIOS: Award Modular BIOS v4.51PG  03/25/99

CPU: AMD K6-2/450MHz 3DX 3DNOW! MMX PC100 BUS CPU

CPU FAN: ARX "CPU Cooler" Socket7 ball bearing Cooling Fan w/heat sink & Thermal Gel

RAM: 384MB Total
(3) Crucial 128MB 168-pin DIMM 16Mx64 8ns 3.3V PC100 SDRAM Unbuffered Non-parity DIMM Part 

HDD: (FAT32)
C:\ Maxtor 91741UA 26.08GB 7200rpm UDMA/66 E-IDE HDD (16.0GB on C:\)
D:\ Western Digital Caviar WD200 20.0GB 7200rpm UDMA/66 E-IDE HDD
E:\ 8.0GB Partition of C:\
   c: (FAT32 on drive 0) 17.40 GB 15.96 GB free
   d: (FAT32 on drive 1) 20.01 GB 19.23 GB free
   e: (FAT32 on drive 0) 8.69 GB 8.69 GB free

FDD: Samsung 1.44MB 3.5" Floppy Disk Drive

CD-ROM DRIVE: CyberDrive 321D 32Xmax Atapi IDE CD-ROM Drive

CD-RW DRIVE: HP CD-Writer 9510i C4503A MYBG5G5Z2A 12x8x32x Multi-Read 4MB/Buffer IDE Drive

VIDEO CARD: STB LightSpeed 3300/3Dfx Voodoo Banshee 128-bit 3D 1X AGP RAMDAC 16MB SGRAM Video Card

LANcard: Intel GD82559 PCI 10/100+ Alert on LAN* Ethernet Adapter Network Card

MODEM: Actiontec 56K/V.90 PCI Pro PCI56019-01 56Kflex Lucent FAX/Data/Voice/Speakerphone Windows Modem

SOUNDCARD: Yamaha YMF-719e-s OPL3-SAx 16-bit 128-Voice 3D WaveTable ISA Stereo Sound Card

CASE: TigerDirect OEM 6-Bay AT/ATX Mid-Tower PC Case w/extra 80mm Front Case Cooling Fan

CASE FAN: ARX 80mm (3.15") 12 Volt ball bearing Front Case Cooling Fan in Rear

POWER SUPPLY: Maxpower 300Watt ATX Power Supply
---

I also run Feisty Fawn v7.04 on a Pentium IV 2.6GHz, blazing fast!

---

### Post by moon2js on 2007-04-29
I dunno about you, but I've got a Pentium 3 running Xubuntu without any major problems. Limited RAM is what slows it down more than proc. I could probably run Gnome on it, too, but I'm using it more as a server.

I've also got an AMD Athlon (1.2-Ghz), and I don't know how that compares to Intel, but I think it may be equivalent or older than the P4. And that's running Feisty with Gnome and KDE well.

Both of these machines were thought to be too old by their original owners, but they never upgraded the paltry on-board RAM that came with these machines. They both came with 128-mb and that's not good enough to do much at all.

If the computers you've got are made by some major OEM like Dell or Gateway, you can get a wealth of information about the original hardware configuration of the machine by entering its serial number on the manufacturer's support site.

---

### Post by aleska on 2007-04-29
Thank you; I will definitely follow your advice and get a better handle on what I really have.  I have a feeling that the two I'm thinking about are in fact both P4's, but I'm not sure they are Giga anything.  Sub 1-GHz processor speed.  Also, the RAM is very low.  

So, if I do in fact have P4's, in general **is it worthwhile **to just go out to the local computer store and buy higher RAM?  Is there a way to upgrade the (er...what do you call the speed? processor speed e.g. to 1.6GHz or higher).  Or is that a motherboard thing that makes it cost prohibitive?  

Apologies in advance for asking questions that make my complete lack on knowledge about hardware so sadly apparent.
Thanks!

---

### Post by moon2js on 2007-04-29
I'm no hardware expert, but I think the Pentium 4 starts at 1.3 GHz. I would not bother trying to upgrade anything but the RAM though.

Like I said, I have a Pentium 3 (500 MHz), and once I upgraded the RAM to 256mb total, it's a perfectly usable Firefoxing, http serving, samba sharing machine. I'm typing from it now, in fact. But if I didn't care about using GUIs, and just used it exclusively as a server, that much RAM is kinda overkill.

RAM can be tricky though because you need to know both what kind of RAM you need and what the configuration/arrangement of RAM in your machine is (so you know how much to buy). Crucial.com is a good resource.

I'd suggest you really check out that the machines do indeed work and whether you'll use them as exclusively a server or not before you upgrade their RAM. The Ubuntu live (desktop) CDs never work on my machines, so I have to use the alternate CD to install. Try Knoppix to make sure everything works. My Ubuntu machines used to hang quite a bit until I adjusted xorg.conf, although I don't think I had to do that with Feisty.

If the two machines use the same type of RAM, you could even scavenge RAM from one to the other. For example, I upgraded one of my computers with a 512-mb RAM module and this computer had only two banks so I had to take out an old 128-mb module. Just took that and doubled the RAM on the aforementioned P3.

---

### Post by aleska on 2007-04-30
Ok. so I was way off.  Both are Pentium II.  Does that make more sense now?  
Anyway, I check the bios on both at boot up.  Here are the details...
PC 1:
Dell Dimension XPS R400
PII / 400 MHz
Cache RAM 512 KB
System Memory 96 MB
Mem Bank 0: 64 MB
Mem Bank 1: 32 MB
Mem Bank 2: Not Installed

PC 2:
Mitsuba
PII / 350 MHz
System Bus Frequency 100 MHz
Cache RAM 512 KB
Total Memory: 256 MB

I notice that the BIOS info was different in detail.  Just looking at these, do they look equivalent?  Would parts from one added to the other actually improve anything (aside from the ethernet card to make a firewall).

Any thoughts on what I've got?
Thanks!

---

### Post by John the train on 2007-04-30
Aleska. Your PC2 looks as if it should run Ubuntu, I'm running Xubuntu Dapper on a Dell Latitude laptop with a 300Mhz p2, 192MB RAM. The Dell I'm not sure about, it might be worth Googling to try and find a spec sheet which could tell you the maximum RAM it will support, or you could try one of the micro-distros like Puppy Linux.

---

### Post by aleska on 2007-04-30
Funny thing, the Dell is old enough that crucial.com's wizard for picking memory doesn't have my pc (XPS R400) as an option.  Looks like similar pcs are going for a whopping $30 on eBay.  Anyway, maybe I should stop thinking about grand plans of resurrecting one of the two pcs into a modern desktop and get back to my initial question.
What about just running a server?  
A PII / 350 MHz with 512 KB Cache RAM and 256 MB Total Memory...sound like enough for a LAMP server?

---

### Post by moon2js on 2007-04-30
Either can be a server. But 256-mb RAM is overkill for a home server, I think.

If I had a P2 with 256-mb RAM, I'd try to run Fluxbox or some really lightweight windows manager. Back when I had the P3 with only 128-mb RAM, I used Xubuntu with Fluxbox. I use Synergy to share mouse and keyboard so my old machine is like a desktop extension.

But if you don't have any need for GUI, just roll a LAMP server.

---

