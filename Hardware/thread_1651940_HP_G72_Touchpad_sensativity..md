---
title: "HP G72 Touchpad sensativity."
date: 2010-12-23
forum: Hardware
---

### Post by Wiz4rd on 2010-12-23
I have a 
**HP G72-259WM**


I am dual booting with win 7 64bit and ubuntu 10.10. This is the first linux that has really worked for me and makes me want to forget windows but I have some issues. One is wifi disconnecting and only a reboot will fix, and wicd ive tried using with the wapsuplicant installed too and its still screwy. Anyways my issue now is the touchpad. It seems super sensative. Like I hover over it while typing and the focus goes awau from what I am typing, I have to drag my cursor back over. Not sure if it is a driver issue or an adjustment but I was hoping some of you fine folks might be able to tell me how I can get this thing to stop being so sensative. If i touch the touchpad with a HAIR it moves. I click an instant message window, start to type, and it clicks something else, I click back, wait a few seconds, then type a BOOK if i want to its all fine. Seems super sensative mostly after I let go of the pad and type.

---

### Post by Wiz4rd on 2010-12-29
Thanks for the help, wonderful support here. LOL.

---

### Post by pi/roman on 2010-12-29
To test different touchpad settings you need to open a terminal and type:
```
synclient -l
```This will show you a list of options to adjust with your touchpad. Some of them are enabled by default on most touchpads and while they usually work normally they an cause problems on other touchpads. The option "fingerhigh" adjusts how heavy your touch is before the touchpad responds, this could affect your sensitivity. The option "tapbutton1" is a switch for turning on|off 1 finger tapping which could cause a click to register if you bump it by mistake. Many of the options that are zero or 1 are switches to turn the option on or off. You can disable tapping completely in system / preferences / mouse on the touchpad tab.

You can adjust the options in synclient by typing in terminal:
```
synclient [COLOR=Purple]OPTION[/COLOR]=[COLOR=Purple]VALUE[/COLOR]
```for instance to set fingerhigh to 40 type:
```
synclient fingerhigh=40
```You can see what all these options do by looking in the synaptics manual:
```
man synaptics
```With regards to your wireless adapter it would be necessary to identify your chipset first. you should be able to find it in the pci bus list:
```
lspci
```

---

### Post by pat_rich on 2010-12-30
I have a HP G72-260, running 10.10

I have the same wifi problem. Disconnection after about  5-10 minutes of each new boot.

my lspci is as follows:

~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller (rev 10)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

Tips are greatly appreciated!

---

### Post by pi/roman on 2010-12-30
This is your wireless adapter:
> 02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller (rev 10)Wiz4rd may not have the same chip so he should check that too. There is a driver for this chip from Realtek's website that I don't believe is installed automatically. You may need to get that. First you should check what driver you are using now. So try this:
```
lsmod | grep -E '(8191|8192)'
```I'm guessing it's the 8192 driver which may work perfectly fine but it could also be causing this problem.  If your driver is r8192se_pci you can restart by the following command so you don't need to restart your computer.
```
sudo modprobe -rv r8192se_pci
sudo modprobe -v r8192se_pci
```

There is a topic on the realtek 8191 here which may contain useful information.
[http://ubuntuforums.org/showthread.php?t=1267961](http://ubuntuforums.org/showthread.php?t=1267961)

---

### Post by pat_rich on 2011-01-28
p { margin-bottom: 0.08in; }   Sorry for the delay, but I've been dealing with the problem more than I've tried fixing it.  I read the links you gave me and they seemed to all say just download the driver, so I tried it.

I have tried installing and reinstalling Realtek's 8191 driver, downloaded from their website.  There are 3 options on the 'downloads' page.

1. rtl8191SU      This one is for USB or something.
2. rtl8191se_va2   Turns out when I download, its the same driver as option #3
3. rtl8192se       I've tried installing and reinstalling with no luck.  The problem is still the same, only one or two minutes of internet, then cut off.  

Also, the modprobe code just causes a freeze, and I have to hold the power button to shut down.

Thank you for your help.

---

