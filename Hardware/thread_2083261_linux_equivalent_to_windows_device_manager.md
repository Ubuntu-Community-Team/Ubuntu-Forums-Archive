---
title: "linux equivalent to windows device manager"
date: 2012-11-11
forum: Hardware
---

### Post by Dougustine on 2012-11-11
is there anything in linux that I can use to show what is installed and working correctly in linux?  MS has device manager with a nice question mark on a section that is not working but I am at a loss to see if my hardware is installed correctly or even working in linux please help me

---

### Post by gerowen on 2012-11-12
I like the program sysinfo , it's basically a nice little hardware profiler.  I'm not sure it will show hardware that isn't working properly though.  There's a package in the software center called "Hardware Lister" that may be what you're lookin for, I know that in the past I've used software that's like what you're looking for.  I just like sysinfo because I know what is in my computer and it gives me some basic info about it if I need to look it up real quick.  Attached are some screenshots for your reference.

---

### Post by Cheesehead on 2012-11-12
A short answer is 'No, Linux is structured differently.'

A more useful answer is 'What hardware do you suspect is not compatible? And what are they symptoms?'

Another useful answer is to try the 'lshw' command. It will show you what the system thinks is installed.

In Windows, you need a Device Manager because installing drivers is generally a user responsibility. The Device Manager is a way to track which drivers you have installed for which hardware. If hardware doesn't work, it's a user responsibility to go find proper drivers and install them. The OS includes a lot of drivers as a convenience to the paying customer.

The Linux goal, on the other had, is that users generally shouldn't need to fuss wth drivers. If hardware doesn't work, that's considered a bug instead of user problem. Additional compatibility is included with most kernel updates.

That's a gross simplification, of course. Users do occasionally need to find workarounds to incompatibility, and some hardware manufacturers refuse to cooperate.

---

### Post by Dougustine on 2012-11-13
Then why do you need to compile drivers?  I have a piece of hardware that lspcii says is there but does not respond properly(haulage wintvhvr2250) I have no idea if I should try to compile a driver for it or not.  Whether this is considered a bug or not a program that can tell you that hardware not operating properly seems like a good idea to me.

---

### Post by dFlyer on 2012-11-13
Your answer is in the above post. A lot of the time a company that created the software will not release the source code and someone else has to create a program that will work and they may only provide the source code, which means your have to compile it for your system. A nice thing about linux is that your free to create your own program.

---

### Post by Dougustine on 2012-11-14
thank you for your help and information, The problem was firmware.  Perhaps my misunderstanding is from windows in which I thought that drivers installed firmware, this has now made me understand both concepts a little more. Unfortunately the lesson took 3 weeks of staying up to midnight, but lesson learned nonetheless

---

### Post by VooDooSyxx on 2012-11-15
From the terminal you can list out your hardware using lspci and lsusb. Should give you something like what's below. Anything listed has been detected by the kernel and in a working state. 

```

$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 6320]
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Wrestler HDMI Audio [Radeon HD 6250/6310]
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Port
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 42)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:15.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:15.3 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB900 PCI to PCI bridge (PCIE port 3)
00:16.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
01:00.0 USB controller: Renesas Technology Corp. Device 0015 (rev 02)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

``````

$ lsusb 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN
Bus 002 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 004 Device 004: ID 046d:c52e Logitech, Inc.

```

---

