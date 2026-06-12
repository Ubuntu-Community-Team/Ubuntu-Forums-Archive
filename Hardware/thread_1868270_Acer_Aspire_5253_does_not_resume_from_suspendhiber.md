---
title: "Acer Aspire 5253 does not resume from suspend/hibernate - black screen"
date: 2011-10-24
forum: Hardware
---

### Post by Aesso on 2011-10-24
I cannot get my Acer Aspire 5253 laptop to properly resume from suspend or to hibernate at all. I've crawled these and other Linux-related forums for the past several weeks, and my attempts to fix this have not been successful. At this writing, I've owned this laptop for about two months now, and it was always my intent to install Ubuntu the minute I got my hands on it. Since I've owned it, it's had Natty and Oneiric installed on it.

The system seems to go into suspend just fine; however, when I try to wake it up, the display does not turn back on. It is otherwise responsive - once it's awake, I can usually [FONT=Courier New]ssh[/FONT] into it from another workstation (assuming the network devices have awakened too), but no display! The keyboard works because I can do REISUB to reboot it. Oddly and much to my dismay, suspend worked perfectly when I booted from a live CD (both 32- and 64-bit versions). I can't figure out why it doesn't work on my full installation. I thought maybe there was an issue with the proprietary graphics driver (fglrx), so I even formatted and did a fresh install to see if it would suspend (and wake up) with the open source ATI driver. Nope, same thing. 

Hibernating doesn't work either. It will attempt to swap to disk and fail, only to come back to the lightdm screen. 

So now I'm back where I started. I have a laptop I can't suspend or hibernate in Ubuntu. Any ideas? Thanks in advance.

A few specs:
AMD C-50 dual-core APU
ATI Radeon HD 6250, 256MB VRAM
8GB RAM

Running Oneiric 64-bit
Linux kernel 3.0.0-12-generic
Swap partition size is 20GB

```
$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 058f:b002 Alcor Micro Corp. 
Bus 003 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
``````
$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Complex
00:01.0 VGA compatible controller: ATI Technologies Inc Device 9804
00:01.1 Audio device: ATI Technologies Inc Wrestler HDMI Audio [Radeon HD 6250/6310]
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:15.0 PCI bridge: ATI Technologies Inc SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:15.2 PCI bridge: ATI Technologies Inc SB900 PCI to PCI bridge (PCIE port 2)
00:15.3 PCI bridge: ATI Technologies Inc SB900 PCI to PCI bridge (PCIE port 3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
06:00.0 Ethernet controller: Atheros Communications AR8151 v2.0 Gigabit Ethernet (rev c0)
07:00.0 Network controller: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) (rev 01)
``````
$ cat /proc/acpi/wakeup 
Device  S-state   Status   Sysfs node
SPB2      S4    *disabled  pci:0000:00:15.2
GEC       S4    *disabled  
USB0      S3    *disabled  pci:0000:00:12.0
USB4      S3    *disabled  pci:0000:00:12.2
P2P       S5    *disabled  pci:0000:00:14.4
```

---

### Post by outofthecave on 2011-10-24
Two things:
1. On my Acer TravelMate 8371, I cannot resume from suspend, either, but in my case, the computer shuts down when I wake it up.  Suspend worked fine in Lucid and Maverick, but in Natty and Oneiric it's broken.
2. I used to have a graphics bug on the same machine, which caused the screen to suddenly go black for no reason.  I can usually fix it quickly by switching to a text terminal (Ctrl+Alt+F1) and back to the GUI (Ctrl+Alt+F7).  I guess that causes the GUI screen to be redrawn.  Probably this could help you too.

---

### Post by Yahoé on 2011-10-24
The problem persists from 11.04. vmajor had opened a bug report months ago [https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/802074](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/802074) but it never got picked up, I guess the developers are swamped with the very long list of bugs affecting Oneiric.

---

### Post by Aesso on 2011-10-24
> **outofthecave said:**
> 2. I used to have a graphics bug on the same machine, which caused the  screen to suddenly go black for no reason.  I can usually fix it quickly  by switching to a text terminal (Ctrl+Alt+F1) and back to the GUI  (Ctrl+Alt+F7).  I guess that causes the GUI screen to be redrawn.   Probably this could help you too.

Thanks. I tried your idea when I got home today. I suspended the machine, woke it up, pressed Ctrl-Alt-F1 hoping for a terminal (nothing), and then Ctrl-Alt-F7 again hoping to see the GUI (nothing). It seemed pretty promising and would have been a workaround I could have dealt with.

I've been doing some more digging and tried this today to see if it would suspend:
[_Re: Suspend/hibernate problems - Kernel? ATI Radeon X300_]("http://ubuntuforums.org/showpost.php?p=11347202&postcount=22")

Unfortunately, that didn't work either. Same symptoms I've already described. 

> **Yahoé said:**
> The problem persists from 11.04. vmajor had opened a bug report months ago [https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/802074](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/802074) but it never got picked up, I guess the developers are swamped with the very long list of bugs affecting Oneiric.
Wow, good catch, and thanks for responding. 

Other than this bug, this has been one of the easiest, most painless installations I've ever had involving Ubuntu (or any other Linux distro) on a laptop, compared to what I went through four years ago with my ThinkPad and Broadcom wireless adapter. It goes to show how far it's come along.

---

### Post by alenp on 2011-11-03
I've fixed this for myself on oneiric by removing the proprietary fglrx ati drivers and defaulting to the open source radeon driver. So far, so good -- 2D and 3D acceleration seems to work perfectly (I don't think my eyes can tell any difference between glxgears at 60 fps and glxgears at 250 fps), and suspend/resume is all good.

I followed the instructions here to make it happen: [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Removing_Catalyst.2Ffglrx)

I have a 5253 with a radeon hd 6310.

---

### Post by ilwage on 2012-04-28
Same issue with my Acer Aspire 5541G, under any linux distro I've tried (Fedora 16, Ubuntu 11.10, Mint 12, and now Ubuntu 12.04). Linux can't wake up after suspension, I just get a black screen and have to force a shutdown.
I've been browsing the web & forums a lot but never managed to find a solution. Hasn't the situation changed since the last post on this thread?

---

