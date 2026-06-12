---
title: "ATI 3200 fglrx screen flicker"
date: 2009-07-15
forum: Hardware
---

### Post by ufmace on 2009-07-15
I've been trying to figure out this problem for a few hours now, with no luck so far. The setup is a Radeon integrated 3200 graphics card on a Gigabyte motherboard with an AMD Phenom II X2 processor, and I'm running Jaunty. The monitor is an Asus VH222. When I first started the computer up using the default open-source drivers, the screen works fine, except for the lack of 2D and 3D acceleration. So I did the automated proprietary driver install, and the results was an accelerated display with a bizarre flickering problem.

It's not exactly flickering, but I don't really know what else to call it. What happens is that a few dozen individual horizontal lines keep jumping about an inch or two to the right and back in various places at a frequency that looks close to the refresh rate. The jumping lines are spread evenly through the height of the display at around 2 or 3 per inch.

So far, I tried swapping the connection to VGA instead of DVI, with no result. I installed the newest fglrx driver using the instructions at wiki.cchtml.com and got better behavior from the driver in some other aspects (google earth seems to work more smoothly), but the flickering was unchanged. I have also used this monitor with a Mac with no problems, but I don't have any other monitors to use with this computer right now.

Does anyone have any idea what's going on or how to fix this? Any other information you want to know?

---

### Post by LepeKaname on 2009-07-15
I was able to run 2D/3D acceleration with the OSS driver. I have the ATI Xpress 200, but may work for you as well...

Check this thread:

[http://ubuntuforums.org/showthread.php?t=1137467](http://ubuntuforums.org/showthread.php?t=1137467)

---

### Post by beanhead on 2009-07-15
Same problem here horizontal lines and slight pixel break up. I installed using the Ubuntu method system>admin>restricted drivers.
card line quote from  lspci output ---- VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
on M3A78-EM mother board 
64 bit AMD 

whole lspci

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: ASUSTeK Computer Inc. Device 9602
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
02:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. IEEE 1394 Host Controller
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)


I am not sure if this is a bug or needs some polishing please make my graphics smooth. Thanks < Ron
:guitar:

---

### Post by ufmace on 2009-07-15
> **LepeKaname said:**
> I was able to run 2D/3D acceleration with the OSS driver. I have the ATI Xpress 200, but may work for you as well...

Check this thread:

[http://ubuntuforums.org/showthread.php?t=1137467](http://ubuntuforums.org/showthread.php?t=1137467)

Are you talking about the RadeonHD driver? It looks like that is only compatible with 500 and 600 series. The built-in 3200 card is a 700 series, so it looks like fglrx is the only option for a fully accelerated driver. The fglrx driver does basically work, there's just this bizarre flickering thing. On the bright side, at least those drivers are getting updated every month or so...

---

### Post by samwisekoi on 2009-08-12
Same problem, same path (worked fine with OS driver, but limited capabilities, so I installed proprietary driver v8.60.40).



Ubuntu 9.0.4 AMD_64
GIGABYTE GA-MA78GM-US2H
AMD Phenom 9600 Agena 2.3GHz Socket AM2+ 95W Quad-Core Processor
Kingston 8GB (2 x 4GB) 240-Pin DDR2 800
2x WD Caviar Black 640GB 7200 SATA (SW RAID 1)
SAMSUNG DVD Burner Black SATA Model SH-S223L LightScribe Support - OEM
512MB Allocated to Video Memory
Single ASUS VGA monitor 1280x1024 (analog D-Sub)
Adding a second display using DVI as soon as it arrives from NewEgg...

And, running under VMware Server 2.0
Windows XP Pro
2 CPU
2GB RAM
40GB Disk Partition

Oddly, the flicker seems less pronounced in the Windows VM, but it still there.  I have *NOT* tried to run the Windows driver in the VM.

I will post an update if I find one.

 - Sam

---

### Post by ufmace on 2009-08-25
Got a bit of an update. I installed a spare NVidia card that I found laying around at the office (a Quadro FX 370), and it seems to work fine. I let Ubuntu do the automatic proprietary driver install, and I have smooth accelerated video. I may have to buy my own low-end NVidia card to get this working properly.

In the meantime, no news on the flgrx drivers, but the RadeonHD drivers may be worth a try. I'll see how well those work the next time I have a while to mess around with my video config.

---

### Post by ufmace on 2009-10-31
Another update - I just upgraded to Karmic, and before I did it, I switched back to the built-in ATI card. After I upgraded, I had it load the proprietary driver again, and now it works fine. I guess it was an X related problem that was fixed somewhere along the line.

---

### Post by pyrokamileon on 2010-04-10
I've had this problem for a while but it never bothered me too much because I had my linksys wireless USB adapter plugged in.  as long as it's plugged in this problem goes away completely.  once or twice when I unplugged it I noticed this problem would crop up but my solution was always to just plug the adapter back in.  well I'm sorry to hear that no one has found a fix for this, just through I'd let you all know how I workaround it...

---

