---
title: "Setting up wireless with broadcom"
date: 2007-10-18
forum: Hardware &amp; Laptops
---

### Post by nickkov89 on 2007-10-18
I have a dual boot HP dv9000, and on my other partition I have Windows Vista. On Vista it says that my card is a Broadcom 802.11a/b/g WLAN. Does anybody have any insight on how to get Ubuntu to read this card? Thanks a lot.

---

### Post by Ayuthia on 2007-10-18
There are two options that you can use.  One is using bcm43xx-fwcutter and the other is ndiswrapper.  How you install it will be based on which version of Ubuntu you are using.  If you are on Gutsy, you can use the linux-restricted-modules for bcm43xx-fwcutter or you can install ndiswrapper through Adept.  In both cases, you will need to be connected to the internet.

If you could, can you post your lspci -nn result along with which version of Ubuntu you are using (please include if it is 32-bit or 64-bit)

---

### Post by nickkov89 on 2007-10-18
This is my lspci -nn is the following: 
It is 32-bit by the way

00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f0] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:05.0 VGA compatible controller [0300]: nVidia Corporation C51 PCI Express Bridge [10de:0244] (rev a2)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1)
00:0f.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0267] (rev f1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
03:00.0 Network controller [0280]: Broadcom Corporation BCM4310 UART [14e4:4312] (rev 02)
07:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd Unknown device [1180:0832]
07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
07:05.2 System peripheral [0880]: Ricoh Co Ltd Unknown device [1180:0843] (rev 01)
07:05.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a)
07:05.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05)

Ill need some more help thanks =D

---

### Post by nickkov89 on 2007-10-18
Ok, new update: I installed the appropriate driver and it says that hardware is present, yet it still doesnt let me get online, whats wrong?

This is what i get using ndiswrapper -l : 

nickk@nick-laptop:~$ ndiswrapper -l
athfmwdl : driver installed
bcmwl5 : driver installed
        device (14E4:4312) present (alternate driver: bcm43xx)
netwg11t : driver installed

---

### Post by Ayuthia on 2007-10-18
```
03:00.0 Network controller [0280]: Broadcom Corporation BCM4310 UART [14e4:4312] (rev 02)
```
Your chipset is 14e3:4312

One part that is missing is which version of Ubuntu you are using.  If you are using Gutsy, the packages you need are on the CD with the exception of the driver.

If you are not using Gusty, here is one option on how to get your wireless card running.
[http://ubuntuforums.org/showthread.php?t=340689](http://ubuntuforums.org/showthread.php?t=340689)
The link is for a 4306 card, but it should work for yours also.  Most people seem to have better results with ndiswrapper.

---

### Post by nickkov89 on 2007-10-18
I am using Ubuntu Fiesty, but i doubt the link you provided will work for me as its for xubuntu unless they're the same?

---

### Post by Ayuthia on 2007-10-18
It is the same.  You will need to change edgy to feisty though and ndiswrapper is now on version 1.48 instead of 1.34

---

### Post by ljonesj on 2007-10-18
ubuntu and xubuntu use the same source from ubuntu

---

### Post by nickkov89 on 2007-10-18
That How-To guide didn't work for me. Some of steps were faulty, like for example , i got to the step of where i have to type -iwconfig , my wireless card is not identified with wlan0. this is so frustrating

---

### Post by nickkov89 on 2007-10-18
well i got somewhere, when i type iwconfig this is what i get:

> lo        no wireless extensions.

eth0      no wireless extensions.

device    IEEE 802.11b/g  ESSID:"r"  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.472 GHz  Access Point: Invalid   
          RTS thr: off   Fragment thr: off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

and when i type ndiswrapper -l i get

bcmwl5 : driver installed
        device (14E4:4312) present (alternate driver: bcm43xx)

im getting somewhere but i read somewhere in the iwconfig file i need to have wlan0 for my bcm4310

---

### Post by Ayuthia on 2007-10-19
You should have either a wlan0 or eth1.

Can you post the following:
ndiswrapper -v
ifconfig
sudo lshw -C network

The first one will provide the version of ndiswrapper that you are using.  I just want to make sure that it was installed ok.  The next step will show if it sees your wireless card.  The third one will also confirm it but it will also display which driver your wireless card is trying to run.

---

### Post by shanerdaner on 2007-10-19
Hi i use gutsy and when I install bcm43xx-0.3.2-internet I install the firmware and the wireless works when i reboot it is off ...just wondering how to make it survive the reboots....
here is my info let me know what else u need!!
00:05.0 VGA compatible controller: nVidia Corporation MCP51 PCI-X GeForce Go 6100 (rev a2)
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
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

---

### Post by Ayuthia on 2007-10-19
> **shanerdaner said:**
> Hi i use gutsy and when I install bcm43xx-0.3.2-internet I install the firmware and the wireless works when i reboot it is off ...just wondering how to make it survive the reboots....
If I recall correctly, you will need to add bcm43xx to the list of modules in /etc/modules.
```
sudo echo bcm43xx | sudo tee -a /etc/modules
```

---

### Post by shanerdaner on 2007-10-19
> **Ayuthia said:**
> If I recall correctly, you will need to add bcm43xx to the list of modules in /etc/modules.
```
sudo echo bcm43xx | sudo tee -a /etc/modules
```
I will try that when I get the fresh install done thanks for your help!!

---

### Post by shanerdaner on 2007-10-20
It worked like a charm thanks!!!!

---

