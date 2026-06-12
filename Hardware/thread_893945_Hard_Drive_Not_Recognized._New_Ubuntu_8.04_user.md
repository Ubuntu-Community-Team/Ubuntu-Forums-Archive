---
title: "Hard Drive Not Recognized. New Ubuntu 8.04 user"
date: 2008-08-18
forum: Hardware
---

### Post by deftek178 on 2008-08-18
Hi.

So i decided to take the plunge and install linux for the first time. I used dos, then win 3.1, 95, 98, xp, and now vista so no prior linux (or osx really) experience. 

After fighting with the livecd version for two days and not being able to get the vast majority of my hardware to work I decided to make a last ditch effort and install the dual-boot in hopes that everything would magically work. (from windows). I know its not a true dual boot but it seems to work the same and on my laptop linux runs way smoother than vista. 

Everything didnt work when i installed it on the harddrive but i was able to get wireless and nvidia drivers working that wouldnt work on the livecd version. So now ive got compiz fusion and all that good **** so im happy.

Problem is that I cant access the other "partition" from linux. On the livecd version I could go into computer and access files on my c: but now when running it off my hardrive It doesnt show up. I have gnome. Any suggessions? 

Specs:

HP 
TX1000z
CPU	AMD Turion 64 X2 Mobile Technology TL-60 / 2.0 GHz processor
OS	Microsoft Windows Vista Home Premium
RAM	2 GB DDR II SDRAM
Display	12.1" WXGA High Definition BrightView Widescreen with Touchscreen (1280 x 800)
Graphics	NVIDIA GeForce Go 6150 graphics
Audio	Altec Lansing speakers and integrated microphone
Hard Drive	160GB (5400 RPM)
Optical Drive	LightScribe Super Multi 8x DVD/RW
I/O ports	

    * 3 x USB
    * 1 x VGA - 15 pin
    * 1 x TV-Out (S-video)
    * 1 x Microphone-in
    * 2 x Headphone (one offering S/PDIF output)
    * 2 x Infrared - IrDA
    * 1 x Modem - RJ-11
    * 1 x RJ-45 LAN
    * 1 x Express Card
    * 1 x notebook expansion port 3

Communications	

    * 10/100/1000 Ethernet
    * 802.11a/b/g/n (draft 802.11n)
    * WLAN
    * Bluetooth





Thanks!

---

### Post by deftek178 on 2008-08-18
lspci:


00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

---

### Post by deftek178 on 2008-08-19
wow... 22 hours and no response. Im really impressed with linux's "thriving community" with everybody "excited" to help with problems...

---

### Post by fogster74 on 2008-08-22
Hi DefTek,

First off - yes, it can be frustrating when you don't get a quick response to Linux posts. I've been an Ubuntu user for three years and still find it frustrating that it's difficult to get help. I'm getting there slowly and it is good to learn something new and it's nice that I'm starting to try to understand other's problems - my advice would be to keep at it, it's a tough learning curve at first but the OS is getting much better all the time...

With regard to your problem, I'm not quite sure what you mean. 

If you click on 'Places', then click 'Computer', what do you see?

Hope we can help... :-)

Steve

---

### Post by Rawton on 2008-08-23
Hello.
First I would like to say im none to sure if im in the right place but I am a new linux user as well, and I just installed linux on my power edge server but, ubuntu is not recognozing my hot swapables i have three that it is not picking up i was wondering if any one knew what I should do. I do appologise again if i Posted in the wrong area it just seemed like a similar issue.

THank you

---

### Post by fogster74 on 2008-08-23
> **Rawton said:**
> Hello.
 I just installed linux on my power edge server but, ubuntu is not recognozing my hot swapables i have three that it is not picking up i was wondering if any one knew what I should do.

Hi Rawton,

I'd suggest it's probably best to start a new thread for you question :-)

With kindest regards (and welcome to the Ubuntu community!)

Steve

---

