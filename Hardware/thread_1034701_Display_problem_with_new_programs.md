---
title: "Display problem with new programs"
date: 2009-01-08
forum: Hardware
---

### Post by Redsunz on 2009-01-08
Hi I am transitioning from Vista to Ubuntu. Mostly just holding back because I'm a windows gamer.  One problem I am having is whenever I install a new game in the add or remove menu I get a invalid format from my monitor/TV.  Then I have to go get a second monitor and connect it to fix the default resolution.  Any one else have this issue?
Specs
AMD Phenom 9600 ATI 4870X2 4gb of ram currently using 80 gb hard drive. I haven't wiped out my 1 tb vista raid 0 with stripping hopefully soon. And most likely the problem LG 37 inch HD LCD model37LG50
:confused:

---

### Post by Redsunz on 2009-01-09
I saw someone with a resolution problem being asked to post lspci.
So here is mine oh yeah my LCD native resolution is 1920X1080 "1080P"
beavis@Tron:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RD790 Northbridge only dual slot PCI-e_GFX and HT3 K8 part
00:02.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port A)
00:07.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port D)
00:12.0 RAID bus controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
01:00.0 PCI bridge: PLX Technology, Inc. Device 8647 (rev ab)
02:04.0 PCI bridge: PLX Technology, Inc. Device 8647 (rev ab)
02:08.0 PCI bridge: PLX Technology, Inc. Device 8647 (rev ab)
03:00.0 VGA compatible controller: ATI Technologies Inc Device 9441
03:00.1 Audio device: ATI Technologies Inc HD48x0 audio
04:00.0 Display controller: ATI Technologies Inc Device 9441
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
beavis@Tron:~$

---

### Post by Redsunz on 2009-02-05
I fixed it!!
I installed the ATI restricted drivers. Then opened a terminal and programmed in the Frequency range of my 37 inch LG.
sudo aticonfig --initial -f
sudo aticonfig --sync-video=on
sudo aticonfig --resolution=0,1920x1080,1600x1200,1360x768,1280x1024,1280x768,1024x768,800x600,640x480,720x400,640x350
sudo aticonfig --hsync=0,31.468-79.976
sudo aticonfig --vrefresh=0,56.25-75.025
sudo aticonfig --vs=on

DO NOT USE THESE SETTINGS UNLESS YOU HAVE A 37LG50 LCD Display!!

---

### Post by nicobeukes on 2009-05-17
I have the same problem, what would you recommend I do for getting my
4870x2 to work in ubuntu 9.04 with the 9.4 ati drivers, I have a samsung sync-master 226bw 22"
I am running ubuntu 8.10 64bit and the 9.4 drivers work like a charm, I have to get the driver working to be able to do the
aticonfig --pplib-cmd "set fanspeed 0 50" command for my peace off mind that the gpu is nice and cool

---

