---
title: "What is the best hardware for a low price Ubuntu HTPC build?"
date: 2014-01-17
forum: Hardware
---

### Post by reformedrunner101 on 2014-01-17
I am interested in building a HTPC with these parts:
[URL="http://www.newegg.com/Product/Product.aspx?Item=N82E16811154091"]
APEX MI-008 Black Steel Mini-ITX Tower Computer Case 250W Power Supply[/URL]
[URL="http://www.newegg.com/Product/Product.aspx?Item=N82E16819113282"]
AMD A6-5400K Trinity 3.6GHz (3.8GHz Turbo) Socket FM2 65W Dual-Core Desktop APU (CPU + GPU) with DirectX 11 Graphic AMD Radeon HD 7540D AD540KOKHJBOX [/URL]

[http://www.amazon.com/Kingston-Modules-1600MHz-Non-ECC-Desktop]("http://www.amazon.com/Kingston-Modules-1600MHz-Non-ECC-Desktop/dp/B0057Q4ADU/ref=sr_1_1?ie=UTF8&qid=1389656021&sr=8-1&keywords=8gb")
[URL="http://www.amazon.com/MSI-Computer-Corp-Motherboard-FM2-A75IA-E53/dp/B00A2VJIQE/ref=sr_1_1?s=electronics&ie=UTF8&qid=1389655138&sr=1-1&keywords=fm2+itx+motherboard"]
Amazon.com: MSI Computer Corp. DDR3 1066 FM2 Motherboard FM2-A75IA-E53: Electronics[/URL]

[Amazon.com : Asus 24x DVD-RW Serial-ATA Internal OEM Optical Drive DRW-24B1ST (Black)]("http://www.amazon.com/Asus-Serial-ATA-Internal-Optical-DRW-24B1ST/dp/B0033Z2BAQ/ref=pd_sim_pc_5")

I have built several machines before and then installed Windows (not by my choice) and have installed Ubuntu on several PCs, maybe someone with more expertise than me could tell me if this hardware will be an excellent pairing with Ubuntu and if it isn't tell me how I can tweak these components for my needs. I am aware of how well the hardware will perform, but I really care about stability (something that was not prevalent on one of my computers with AMD 6450 graphics out of the box). Thanks in advance for any help!

---

### Post by TheFu on 2014-01-17
$170 is what my HTPC cost 18 months ago. It runs XBMC and uses an AMD E350 APU - 4G RAM and old HDD I had laying around. Media files are stored on different machines on the wired GigE network.  Wifi isn't so good for streaming content. It cannot record TV, not enough power, but thanks to a built-in Radeon GPU, it handles 1080p videos great.

The PSU that came with the APU/MB+Case ($100 combo) was noisier than a jet engine. Louder than most servers, so it had to be replaced.  It is silent now thanks to a picoPSU (google that).  Kill-a-Watt says it uses 26W during playback of hidef stuff.  Turns out that XBMC uses more CPU than video playback due to design considerations made for the original xbox hardware.

I would suggest that instead of starting with parts, that you start with the software and locate recommended, COMPATIBLE, parts from the forums where that software is hosted. It will save you a bunch of trouble.  I found a guy in France who was obsessed with almost the same hardware I had and posts updates to make XBMC purrrrr with it. Without his website, I don't know if the solution would be nearly as easy to get working. Lots of little things to know --- HDMI audio, standby scripts, dealing with multiple video outputs (TV and projector), and don't get me started about remote control settings. Following someone elses guide really will save weeks, if not months of effort.

My XBMC machine is 100% controlled by the remote - no keyboard is connected. When it is time to patch, I ssh in.

Tried to get tvheadend working, but it just made the entire OS crash. Might be more stable now.  If you must have a tuner, please, please consider the HD-Homerun line of network tuners. I have 2 dual HDHR3s on my network. Any computer can access the tuners, which is much more convenient than having a PCIe card stuck inside 1 PC.

---

### Post by z7APXKm on 2014-01-17
FWIW here's mine:

[LIST]
[*]Case - Chieftec Hi-Fi HM03B
[*]MOBO - Asus P8H77-M PRO Intel H77 Socket 1155 Motherboard
[*]CPU - Intel Core i3 3220 Ivy Bridge Dual Core Processor - Retail
[*]CPU FAN - Zalman CNPS8000B Ultra Quiet Low Profile CPU Cooler
[*]Tuner - TBS PCI-E DVB-T2 Dual TV Tuner Card
[*]Disk - Western Digital WD20EARX 2TB Caviar Green Quiet SATA 6Gb/s
[*]PSU - be quiet! BN104 Pure Power L7 350W Power Supply
[*]RAM - Corsair Memory XMS3 Classic 4GB DDR3 2000 MHz Dual
[*]DVD - BDC-207DBK Blu Ray Rom / DVDRW writer from Pioneer
[*]KB/MSE - Cideko AVK08 Air Conqueror Gaming Joypad & Media Centre Keyboard
[*]WEBCAM - Logitech C270 HD Webcam
[/LIST]

---

### Post by smuggly on 2014-01-19
All the hardware you have listed I have too. You may want to think about another case. That one doesn't cool very well. Maybe go for the  coolermaster 130 elite.(Same Price) Everything else looks good. I have exactly the same setup Except I have a 5300 trinity CPU. Works great with XBMC.
You can do better $$ wise on the Board also.

---

