---
title: "Atheros ar9002wb-1ng wifi doesn't work"
date: 2013-09-03
forum: Hardware
---

### Post by henri2 on 2013-09-03
[COLOR=#333333][FONT=UbuntuRegular]Hello!
I installed 13.04 Ubuntu on my Asus U82U today and I can't find a way to fix the problem.I've tried almost everything, even reinstalled and tried on Linux Mint. Wifi worked fine with Windows 8. 
[FONT=Arial]Integrated 802.11 b/g/n and W8 named my card [/FONT][COLOR=#222222][FONT=Verdana]Atheros ar9002wb-1ng.  Laptop - Asus U82u  [/FONT][/COLOR][/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Any suggestions?

I've tried everything I found on internet, but no use. It's my last call for help. Never ever had any of those issues with other laptops
```
[COLOR=#222222][FONT=Verdana]00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Complex[/FONT][/COLOR]
```[/FONT][/COLOR]```

    00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 6320]
    00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Wrestler HDMI Audio [Radeon HD 6250/6310]
    00:04.0 PCI bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Port
    00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (rev 40)
    00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
    00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
    00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
    00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
    00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 42)
    00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
    00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
    00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
    00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40)
    00:15.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
    00:15.1 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1)
    00:15.2 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB900 PCI to PCI bridge (PCIE port 2)
    00:15.3 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB900 PCI to PCI bridge (PCIE port 3)
    00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
    00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
    00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
    00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
    00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
    00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
    00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
    00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
    04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5289 (rev 01)
    04:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller (rev 0a)
    05:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
[COLOR=#333333][FONT=UbuntuRegular][COLOR=#222222][FONT=Verdana]    06:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (       PCI-Express) (rev 01)[/FONT][/COLOR][/FONT][/COLOR]
```[COLOR=#333333][FONT=UbuntuRegular]
[/FONT][/COLOR]
```
sudo rfkill list


    0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
    1: asus-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
    2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
    3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
```
[COLOR=#333333][FONT=UbuntuRegular]
I posted same topic on askubuntu too, but nobody was able to help me. I've tried turning wifi on via hardware switch, even removed ethernet cable.
Thank you![/FONT][/COLOR]

---

