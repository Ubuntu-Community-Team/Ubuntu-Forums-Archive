---
title: "Bose Companion 5 USB Speakers - Buzzing Sound"
date: 2016-07-02
forum: Hardware
---

### Post by Shibblet on 2016-07-02
Please, please. please, help!

I have been posting about this for years now.  Ever since Ubuntu 13.04.  I have a pair of Bose Companion 5 Speakers, and they don't work in Ubuntu.

The system recognizes that they are there, and as far as ubuntu is concerned, they work just fine.  But when they playback any kind of sound,they make this terrible buzzing noise instead of the sound they are supposed to play.

I don't know what is causing this, but I can't use Ubuntu, and I've been stuck with Windows.

Does anyone know how to fix this?

---

### Post by him610 on 2016-07-04
Not the fault exclusively of Bose Companion 5 speakers; this happens to speakers from other manufacturers also. That buzzing noise you hear is probably from your 60 Hz AC power.

Recommend you check the wiring to the speakers - both power and audio. Make sure wires do not run close to other AC wiring. You may need to reroute your cables  You also may need to replace the audio wiring with shielded wiring. Avoid rolling your excess wiring into a coil, better to wrap it in a figure 8.

---

### Post by Shibblet on 2016-07-05
I appreciate you helping me in this situation.  You're the first person to even offer a solution in 3 years (see the threads below).

But it is not due to the power supply.  There is absolutely no buzzing in Windows, and the Bose Companion 5 (USB) Speakers aren't just buzzing overtop of the sound, the sound playback sounds like it is being stretched out and distorted.

I have had this problem ever since Ubuntu 13.04.  Which means I have been unable to solve this, or use Ubuntu for over 3 years at this point. 

See these threads:
[http://ubuntuforums.org/showthread.php?t=2283830](http://ubuntuforums.org/showthread.php?t=2283830)
[http://ubuntuforums.org/showthread.php?t=2139854](http://ubuntuforums.org/showthread.php?t=2139854)

I would love there to be some solution, but it seems as if there isn't.

It's funny.  Usually people make excuses to stick with Windows.  I truly want to switch, but that would require me to get new speakers, and run them through my internal sound card.   And I really like the sound that comes out of these speakers, it's amazing.

---

### Post by X-RED_Tech on 2016-07-05
So it worked before 13.04? Are you absolutely sure?

I've noticed that some specialized USB audio hardware isn't fully supported in Linux but that's rarely the case of speakers. BOSE does not support Linux, people have to learn to live with it.
That said, if it was working before there's no reason why it shouldn't now. I would report it as a bug (regression) but unsure against what to report.

---

### Post by him610 on 2016-07-05
Well, now that we have this thread going, we should continue it. Maybe we can figure something out. 
Do you happen to have florescent lights nearby?

What are your system specs? How about showing the results of ```
lspci && lsusb && inxi -F
```

Are these similiar to your speakers?
[https://www.amazon.com/Bose-Companion-Multimedia-Speaker-System/dp/B000IE8Z4Q/ref=sr_1_1?ie=UTF8&qid=1467763247&sr=8-1&keywords=bose+speakers+companion+5]("https://www.amazon.com/Bose-Companion-Multimedia-Speaker-System/dp/B000IE8Z4Q/ref=sr_1_1?ie=UTF8&qid=1467763247&sr=8-1&keywords=bose+speakers+companion+5")

---

### Post by Shibblet on 2016-07-21
Okay, here is the results of "lspci && lsusb && inxi -F"

```
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.4 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 5 (rev c4)
00:1c.5 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c4)
00:1c.6 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 7 (rev c4)
00:1c.7 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 8 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Z77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series/C210 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GK110B [GeForce GTX 780 Ti] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GK110 HDMI Audio (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 09)
04:00.0 PCI bridge: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge (rev 03)
06:00.0 SATA controller: Marvell Technology Group Ltd. 88SE9120 SATA 6Gb/s Controller (rev 12)
07:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
Bus 002 Device 004: ID 413c:2107 Dell Computer Corp. 
Bus 002 Device 003: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 1058:1130 Western Digital Technologies, Inc. My Book Essential (WDBACW)
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 002: ID 05a7:1020 Bose Corp. 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 054c:0243 Sony Corp. MicroVault Flash Drive
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
System:    Host: kubuntu Kernel: 4.4.0-21-generic x86_64 (64 bit)
           Desktop: KDE Plasma 5.5.5 Distro: Ubuntu 16.04 xenial          
Machine:   Mobo: ASUSTeK model: P8Z77-V LE PLUS v: Rev X.0x               
           Bios: American Megatrends v: 0910 date: 03/18/2014
CPU:       Quad core Intel Core i7-3770 (-HT-MCP-) cache: 8192 KB 
           clock speeds: max: 3900 MHz 1: 1602 MHz 2: 1600 MHz
           3: 1599 MHz 4: 1599 MHz 5: 1603 MHz 6: 2001 MHz 7: 1600 MHz
           8: 1599 MHz
Graphics:  Card: NVIDIA GK110B [GeForce GTX 780 Ti]
           Display Server: X.Org 1.18.3 drivers: nouveau (unloaded: fbdev,vesa)
           Resolution: 1920x1080@60.00hz
           GLX Renderer: Gallium 0.4 on NVF1
           GLX Version: 3.0 Mesa 11.2.0
Audio:     Card-1 Intel 7 Series/C210 Series Family High Definition Audio Controller
           driver: snd_hda_intel
           Card-2 NVIDIA GK110 HDMI Audio driver: snd_hda_intel
           Card-3 Bose driver: USB Audio
           Sound: ALSA v: k4.4.0-21-generic
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169
           IF: enp3s0 state: up speed: 1000 Mbps duplex: full
           mac: 60:a4:4c:2c:e3:65
Drives:    HDD Total Size: 8655.7GB (0.0% used)
           ID-1: /dev/sda model: Samsung_SSD_840 size: 512.1GB
           ID-2: /dev/sdb model: Samsung_SSD_840 size: 500.1GB
           ID-3: /dev/sdc model: WDC_WD6400AAKS size: 640.1GB
           ID-4: /dev/sdd model: WDC_WD4000F9YZ size: 4000.8GB
           ID-5: USB /dev/sde model: Storage_Media size: 2.0GB
           ID-6: USB /dev/sdf model: My_Book_1130 size: 3000.6GB
Partition: ID-1: / size: 7.9G used: 340M (5%) fs: overlay dev: N/A
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 29.8C mobo: 27.8C gpu: 31.0
           Fan Speeds (in rpm): cpu: 0
Info:      Processes: 256 Uptime: 3 min Memory: 1100.4/15991.9MB
           Client: Shell (bash) inxi: 2.2.35 
```

And here is a link to a phone video of the actual problem.
[https://www.youtube.com/watch?v=eBIz3Q6JVvg]("https://www.youtube.com/watch?v=eBIz3Q6JVvg")

---

### Post by him610 on 2016-07-22
[https://www.bose.com/en_us/products/speakers/stereo_speakers/companion-5-multimedia-speaker-system.html]("https://www.bose.com/en_us/products/speakers/stereo_speakers/companion-5-multimedia-speaker-system.html")

> Most Helpful Critical Review
Review by hankiebj. Written 11 months ago. 3 out of 5 stars. 
Not really good for computers
The problem I've encountered is that they only use the Microsoft Drivers only. If you are capturing … Show Full Review


Unless you can figure out how to convert the MS drivers, it is probably a lost cause.:(

From the same page...
> For optimum performance, we recommend Windows 7, Windows Vista or Windows XP. For Macintosh computers, OS 10.4 or later.

Bose also makes a set of speakers made for PCs. They sell for about $100. I had a set, but gave them to a relative and settled on headphones for private listening, and a bluetooth speaker for shared listening.

---

