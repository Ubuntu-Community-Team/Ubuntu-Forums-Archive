---
title: "can't turn rtl8187b wlan card on under ubuntu 9.04 in Advent 9315"
date: 2009-07-07
forum: Hardware
---

### Post by xbarranco on 2009-07-07
Hello,

I have a Advent 9315 (model U50SI1) laptop with an internal RTL8187B LAN Card (I guess this: Ubuntu says it's a Ralink RT2501USB but I have found exactly the same architecture in several pages with a RTL8187B card), where I have just installed a dual-boot system with Ubuntu 9.04 and Windows XP. The card works fine out of the box under Windows. Under Ubuntu too, but here I have an issue that I would like to solve with your help. Given that the FN+F10 hotkey combination to toggle the wifi doesn't work under Ubuntu (the card doesn't appear at all in the list of usb or pci devices), everytime I want to use the card I must restart the computer, go to Windows, press FN+F10 to turn the card on, restart again, and finally go to Ubuntu. The card then works fine, but in an unusual way, because the rt73usb module is loaded, not the rtl8187b one. I can connect to my wlan with proper speed.

I have noticed that under Ubuntu indeed, when the card is on, if I press FN+F10 the card goes off, but further FN+F10 keystrokes doesn't turn it on again.

During the installation my only chance to get Ubuntu work in this laptop was setting the  noapic nolacpi acpi=off settings. I have heard that that choice can be causing the FN problems.

My question is: is there any way to activate your internal wlan card under Linux without using the FN hotkeys?

I would appreciate very much your help. Thanks.

____

$ lsusb (after activating the card under windows)
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 002: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

---

### Post by shatterblast on 2009-07-07
As for the reason that Ralink RT25000 may be listed, it's common in the computer hardware industry to buy on-board firmware from a single business that specializes in it after a company gives specifications for its needs.  It's kind of like how a vehicle may have parts from many different companies even though it has only one official name-brand to represent it.  Also in that regard, it's a reason that repairs for computers or vehicles can use parts from supposedly third-party entities.  Shopping wisely gives the benefit of access to high quality parts tagged under different names, which translates to lower prices for you.

Since much of the "wi-fi" wireless technology still runs off of the firmware-cutter thing, it still uses items designed for Windows in a Linux environment.  Basically, the best idea is to connect a wire to your system for your Internet and update your wireless drivers.  The following from Karmic may help your Jaunty or whatever your version:

[http://packages.ubuntu.com/karmic/rt2500-source](http://packages.ubuntu.com/karmic/rt2500-source)

---

### Post by xbarranco on 2009-07-08
Thanks for your suggest! 

I will try to install that driver and paste the results later...

To be honest I am only guessing when I say that Jaunty misidentifies the chipset of my wlan card. Maybe I am wrong, but the fact is that I have found a couple of posts talking about the same problem in laptops with exactly the same architecture as mine...

hardware4linux.info/system/3276/

except for the wireless card. See for example:

ubuntuforums.org/archive/index.php/t-1038576.html

The fact is also that I haven't found anywhere that architecture with a Ralink 2500 usb, as Jaunty says. To check my guess I will also try to install the RTL8187B linux driver and blacklist the others.

---

### Post by xbarranco on 2009-07-11
Finally Google gave answer to my prayers: updating the notebook BIOS was the solution.

The most significant feature of the new BIOS is that the wireless is ON by default... \\:D/

[http://forum.novatech.co.uk/showthread.php?t=4230](http://forum.novatech.co.uk/showthread.php?t=4230)

This update works specifically for model U50SIx (where x=number) notebooks. See the bottom of your notebook to check it out. Follow the instructions. Mine is a U50SI1 and I have done the BIOS flashing with no issues. Now the wireless is always ON at boot. Of course the combination FN+F10 still doesn't work under Ubuntu, but I can as usual turn the wifi activity off through network-manager or similar.

Should I add the [SOLVED] mark to the post title?

Carlos

---

