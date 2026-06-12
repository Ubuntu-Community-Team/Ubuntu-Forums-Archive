---
title: "Screen Resolution"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by Justbill on 2009-10-31
Hello All,

I upgraded this morning from 9.04 to 9.10. The only problem so far are my screen resolutions. The best I can get is 800 x 600. When I was running 9.04 on this same machine (Compaq SR1426NX, with a Compaq FS7600 monitor) I could use screen resolutions of 1024 x 768 or better. 
Can someone tell me how I might get those screen resolutions back?

Thanks in advance
Bill

---

### Post by jtravnick on 2009-10-31
What video card is in your system? Do you have the drivers for it installed?

---

### Post by Justbill on 2009-10-31
Thanks, its the Intel "on-board" video

---

### Post by Wielkitb on 2009-10-31
```
lspci
```
Paste the output related to your graphics card here (VGA compatible controller, or something)... or Google it and try to find a compatible Linux driver.

---

### Post by Justbill on 2009-10-31
here it is (lspci)

bill@bill-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:05.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
bill@bill-desktop:~$ 


Thanks

---

### Post by Wielkitb on 2009-10-31
I can only think of 3 ways to solve your problem... If anyone has a better idea, please post it.

1: You can edit your Xorg.conf file in order to change your resolution. You might want to follow [_this thread_]("http://ubuntuforums.org/showthread.php?t=83973"). There's even an "integrated Intel graphics card" section in it.
**OR**
2: You can download the Linux driver [_here_]("http://intellinuxgraphics.org/download.html") and compile it. There's an installation guide in [_here_]("http://intellinuxgraphics.org/install.html").
**OR**
3: You can get a Windows driver and install it using Ndiswrapper. Download it [_here_]("http://sourceforge.net/projects/ndiswrapper/files/"). There's a wiki [_here_]("http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page"), it will answer any questions you have. It seems like it's a long and hard job, but it's really quick and easy... it's very intuitive.

Hope it helped.

---

### Post by macogw on 2009-10-31
Go with #1. #2 & #3 are silly since Intel graphics drivers are included.

---

### Post by Justbill on 2009-10-31
Well, I looked at #1. My xorg.conf file doesn't really look anything like what is shown in the thread.
This really is kind of ridiculous! In 9.04, everything "auto detected" no problems! If 9.10 can't at least keep the same standard as the previous version........don't call it an "upgrade"

---

### Post by setinggil on 2009-11-01
I have tried Ubuntu 9.10 (without installing) and get screen resolution max 800 x 600. How can I get higher screen resolution?
These are lspci output :

setinggil@mine:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:09.0 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
00:09.1 SD Host controller: ENE Technology Inc ENE PCI SmartMedia / xD Card Reader Controller
00:09.3 FLASH memory: ENE Technology Inc ENE PCI Secure Digital / MMC Card Reader Controller
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
00:1f.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)
setinggil@mine:~$

tia

setinggil

---

### Post by jwang on 2009-11-01
I think the HowTO is incorrect in Karmic, as dpkg-preconfigure is not working for X anymore. The command that works is Xorg -configure.

With regards to xorg.conf format, I don't think it's changed - spend some time on your old xorg.conf and compare to the new generated xorg.conf, you'll see my point.

---

### Post by Justbill on 2009-11-01
Well, this is retarded! 

I just took my box apart, tried to put in a video card (e-GeForce FX 5200), would not work AT ALL (blank screen, and yes, I did reset things in the set up). Took the video card out, decided to blow out the SMALL amount of dust in the box, restarted, and now I have 1024 x 768. HUH :confused:

---

### Post by Justbill on 2009-11-01
Also, I did go to Synaptic Package Manager and add "xserver-xorg-core-dbg. So when I restarted the computer that may have had something to do with it. I dunno#-o

---

### Post by setinggil on 2009-11-01
I have fresh install & fix my problem.
Tks testar12 ([http://ubuntuforums.org/showpost.php?p=8127835&postcount=257]("http://ubuntuforums.org/showpost.php?p=8127835&postcount=257")) for the info.

---

### Post by Keith! on 2009-11-02
I'm getting a 800 x 600 resolution, have tried an new install onto another partition & still same problem.
Was OK initially when the Grub loader wasn't updated with the new kernal, other problems with that.

---

### Post by Justbill on 2009-11-10
For some unknown reason (I suspect it was an update), my screen resolution has reverted back to 800x600, or 640x480.
What's really amazing is, it seems a lot of people are having this same problem (after looking at many threads), and there doesn't seem to be a real good solution. WTF?#-o

---

### Post by Justbill on 2009-11-12
FIXED! I have 1024x768 now! I had to edit /etc/X11/xorg.conf , but it worked! 
Had to use a combination of instructions, but here is a copy of my /etc/X11/xorg.conf file now.

Section "Device" 
	Identifier	"Configured Video Device" 
EndSection 

Section "Monitor" 
	Identifier	"Configured Monitor" 
        [I]Modeline        "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync 
        Option          "PreferredMode" "1024x768_60.00" [/I]
EndSection 

Section "Screen" 
	Identifier	"Default Screen" 
	Monitor		"Configured Monitor" 
	Device		"Configured Video Device" 
        [I]DefaultDepth    24 
        SubSection "Display" 
                Depth             8 
                Modes             "1024x768" "1280x1024" "800x600" "640x480" 
        EndSubSection 
        SubSection "Display" 
                Depth             16 
                Modes             "1024x768" "1280x1024" "800x600" "640x480" 
        EndSubSection 
        SubSection "Display"      
                Depth             24 
                Modes             "1024x768" "1280x1024" "800x600" "640x480" 
        EndSubSection [/I]
EndSection


What is in italics is what I added. What is under "device" is what I changed first, and that didn't make a difference. What I added under "monitor" (in italics) made the difference, thats when it worked.

This has been a huge pain in the *****! I still can't understand why in the older versions of Ubuntu there weren't any problems like this, and then the "new and improved version (9.10) is big problems.

---

### Post by osana412 on 2009-11-19
I have a problem, how to change to be 1366x768 resolution, because I use laptop with wide screen, my video card is SIS 671. I have used 1024x678 using Xorg.conf (vesa) and my screen is stretch. Thnx.

---

