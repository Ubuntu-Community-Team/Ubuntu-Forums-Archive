---
title: "Hardy Heron"
date: 2008-11-18
forum: General Help
---

### Post by tefybaez on 2008-11-18
Sup every1
yesterday i installed ubuntu on my pc (hardy heron) but it doesnt seem to be working right. The screen looks totally weird, like if it was scratched or something (i cant really explain, but it doesnt work right). My guess is the drivers arent installed, or not installed correctly. Also, when i try to use the effects it says "Desktop effects couldnt be enabled", and my internet gets incredibly slow when im using ubuntu, almost as if there was no internet.
I have a SIS 965L board, is there a compatibility issue with ubuntu and this board ?? (my guess is yes though id love it if it was no)


Edit: 
All I can tell from the top of my head is its an SiS 761GX/965L board with AMD Sempron (I know it sucks). Its 1.8 GHz and 1gb RAM. SiS Mirage Graphics. Ill post a fuller spec when I get home.
The OS I'm running (dual boot) is Windows XP SP3, it works perfectly.


(I noticed the video glitch happens when the resolution is bigger than 1024 x 768. When im on windows i use 1280 x 1024.

---

### Post by mikewhatever on 2008-11-18
Please use a more descriptive titles for your threads.
Can you post the output of the following command from Applications->Accessories->Terminal:
sudo lshw -C display

---

### Post by tefybaez on 2008-11-18
Sorry about the title!
i did lspci, here's what i got, if its of any use. Ill be posting what you asked for in a second:


tefybaez@Stefany:~$ sudo lspci 
[sudo] password for tefybaez:  
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 761/M761 Host (rev 02) 
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202 
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS965 [MuTIOL Media IO] (rev 48) 
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01) 
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0) 
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) 
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) 
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) 
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller 
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 190 Gigabit Ethernet Adapter 
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge 
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge 
00:08.0 IDE interface: Silicon Integrated Systems [SiS] Unknown device 0183 (rev 01) 
00:0a.0 Modem: ALi Corporation SmartLink SmartPCI561 56K Modem 
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration 
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map 
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller 
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control 
00:1f.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge 
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter (rev 03) 
tefybaez@Stefany:~$

---

### Post by tefybaez on 2008-11-18
display UNCLAIMED
description: VGA compatible controller
product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
vendor: Silicon Integrated Systems [SiS]
physical id: 0
bus info: pci@0000:01:00.0
version: 03
width: 32 bits
clock: 66MHz
capabilities: pm agp agp-3.0 cap_list
configuration: latency=0


Here's what you asked!

---

