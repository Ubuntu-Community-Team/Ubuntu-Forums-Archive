---
title: "Asus K20DA with AMD APU Quad Core &amp; radeon r3 graphic card."
date: 2017-01-29
forum: Hardware
---

### Post by Portaro on 2017-01-29
In the last week I Buy this new pc [http://www.asus.com/Tower-PCs/K20DA/ ]("http://www.asus.com/Tower-PCs/K20DA/")

lspci &#8594;

> $ lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1566
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Mullins [Radeon R3 Graphics]
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Kabini HDMI/DP Audio
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 156b
00:02.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:02.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:08.0 Encryption controller: Advanced Micro Devices, Inc. [AMD] Device 1537
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 11)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 42)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 02)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1580
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1581
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1582
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1583
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1584
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1585
01:00.0 USB controller: ASMedia Technology Inc. ASM1142 USB 3.1 Host Controller
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 11)



This pc comes with Windows 10 and I install GNU/Linux - Ubuntu and this task works very well, n problems with Bios , only I need to make an USB bootable with Unetbootin and then press F2 on boot to access BIOS, when in the BIOS options all I need to do was choose USB boot with Other OS support option active and then simply install Ubuntu and run it without any problem.

The only thing that you need have in attention is the R3 radeon graphic card because for proprietary drivers you need to use Ubuntu 14.04 ... releases.

All works very well and fast.

I hope that this info can help others if they need choose a new machine , this computer is very cheap so maybe people think in buy it and have this info here to find and view  if GNU/Linux works or not in the hardware, and in conclusion he works very well.

You can view how Lubuntu runs in the PC on this videos , with compiz, stress test to APU with open many softwares and custom actions like video on background &#8594; 
[https://youtu.be/neqV0hThvNQ](https://youtu.be/neqV0hThvNQ)
[https://youtu.be/lRTtZ4EgI6c](https://youtu.be/lRTtZ4EgI6c)

---

