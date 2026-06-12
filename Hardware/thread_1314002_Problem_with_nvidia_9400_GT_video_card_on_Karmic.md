---
title: "Problem with nvidia 9400 GT video card on Karmic"
date: 2009-11-04
forum: Hardware
---

### Post by lokutus25 on 2009-11-04
Hi all, I had an nvidia 8400 video card when I did the upgrade from Jaunty to Karmic. Everything worked fine and my machine was ok.
After that, I had the insane idea to replace the nvidia card with a 9400 GT.
Well...I'm not able even to load the nvidia.ko kernel module.
I tried to remove all the nvidia-glx-xxx drivers and removed the xorg.conf file. Then I reinstalled with aptitude the nvidia-glx-185 (with dependency) drivers that should support the 9400 GT. The dkms work fine and build the new nvidia.ko kernel module but also this module can't be loaded into the kernel.
Here the output of commands:
> 
# modprobe nvidia
FATAL: Error inserting nvidia (/lib/modules/2.6.31-14-generic/updates/dkms/nvidia.ko): No such device

# dmesg
[  194.072261] NVRM: This PCI I/O region assigned to your NVIDIA device is invalid:
[  194.072263] NVRM: BAR1 is 0M @ 0x0 (PCI:0002:00.0)
[  194.072267] NVRM: The system BIOS may have misconfigured your GPU.
[  194.072275] nvidia: probe of 0000:02:00.0 failed with error -1
[  194.072305] NVRM: The NVIDIA probe routine failed for 1 device(s).
[  194.072309] NVRM: None of the NVIDIA graphics adapters were initialized!

# lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. P4M890 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. P4M890 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. P4M890 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. P4M890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
02:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9400 GT] (rev a1)
04:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)


I know that the output of dmesg is suspicious...but I don't know how to deal with it.
Does anyone has suggestions?!
ThanxAll!

---

### Post by lokutus25 on 2009-11-04
Well...I solved in another insane way: the Nvidia 9400 GT card I was trying was the "silent" version. So I changed it with the non silent version and it worked with the nvidia-glx-185 drivers. Maybe the video card in my hand have some problem.
ThanxAll

---

### Post by canadrian on 2009-12-18
I'm having this issue too. Pain in the ***. Do I really need to figure out what to do with this card I just bought, and try to find another PCI or AGP video card with a 9xxx series NVidia chipset? I'm trying to make a cheap VDPAU-capable XBMC box. Here's my lspci and uname -r:

lspci 00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01) 00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01) 00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01) 00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01) 00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01) 00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01) 00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81) 00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01) 00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01) 00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01) 00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01) 01:04.0 PCI bridge: PLX Technology, Inc. PEX8112 x1 Lane PCI Express-to-PCI Bridge (rev aa) 01:07.0 Ethernet controller: Coreco Inc Device 8139 (rev 10) 01:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) 02:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9400 GT] (rev a1)

uname -r 2.6.31-16-generic

---

### Post by Phil Urich on 2009-12-18
> **canadrian said:**
> I'm having this issue too. Pain in the ***. Do I really need to figure out what to do with this card I just bought, and try to find another PCI or AGP video card with a 9xxx series NVidia chipset? I'm trying to make a cheap VDPAU-capable XBMC box. 


Does your dmesg output have any of the same errors as lokutus25's did?

After it starts and fails, have you tried manually (re)starting X with "sudo service restart gdm" or the like?  I know with my setup for awhile there was some bug which left me at the X error screen whenever I started up, but if I hit cancel and got to the prompt I could just issue "sudo service restart kdm" and tada, X would be working again and the login screen would pop up.

---

