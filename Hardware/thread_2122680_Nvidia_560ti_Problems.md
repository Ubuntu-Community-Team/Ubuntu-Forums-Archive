---
title: "Nvidia 560ti Problems"
date: 2013-03-05
forum: Hardware
---

### Post by Jaboba on 2013-03-05
So i have looked at ALOT of threads about nvidia drivers and tried many of the solutions found in them. nothing has worked. 

i have built a desktop and a friend gave me his PNY 560ti graphics card so i put it in my desktop. it worked great with windows but i switched my desktop to Ubuntu to have the Same OS on my desktop as my laptop.
i have only been using linux for a about 9 months. 

i am running Ubuntu 12.10
Using a PNY Nvidia 560ti Graphics Card

The issue is i cant use the card at all, no display comes from it what so ever, before or after nvidia driver installation.
Additional Drivers doesn't show anything is being used.

but if i use the terminal command lspci i get:

```
jaboba@jaboba-PC:~$ lspci
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1c.4 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c4)
00:1c.7 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 8 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Z77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series/C210 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
**01:00.0 VGA compatible controller: NVIDIA Corporation GF114 [GeForce GTX 560 Ti] (rev a1)**
01:00.1 Audio device: NVIDIA Corporation GF114 HDMI Audio Controller (rev a1)
03:00.0 Audio device: Creative Labs Device 0012 (rev 01)
04:00.0 SATA controller: ASMedia Technology Inc. ASM1062 Serial ATA Controller (rev 01)
05:00.0 PCI bridge: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge (rev 03)
07:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
```

i am very frustrated with trying to get this to work and am currently only running off Intel graphics but i would like to use my desktop for gaming. 
ANY help would be very much appriciated.

---

### Post by wribeiro on 2013-03-06
I'm sorry to say that your disappointment is shared by many people. The experience of Ubuntu with nVidia is a frustration for most users and the development of the open source driver does not seem to be a priority.

Here are some of my pain with nVidia:

- [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/568492](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/568492)
- [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-updates/+bug/1144232](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-updates/+bug/1144232)
- [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/752445](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/752445)
- [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1085124](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1085124)
- [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/538275](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/538275)
- [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/575092](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/575092)

---

### Post by Jaboba on 2013-03-06
so what i'll probably do this weekend is dual boot my desktop with windows again.

Don't want to have to do this but i guess it is the only solution im seeing right now. hopefully in the near future there will be better support

All we can do is hope

---

### Post by wribeiro on 2013-03-07
I have ever tried to avoid having dual boot with Windows, but honestly, it's impossible when you have a nvidia card.
This problem is very serious, it became worse after Unity interface and has caused rejection among new users.
Unity is a great environment, but is not well integrated with the nVidia Driver.

---

