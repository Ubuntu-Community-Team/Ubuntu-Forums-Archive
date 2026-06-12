---
title: "Need help"
date: 2005-12-19
forum: Installation &amp; Upgrades
---

### Post by skyhigh007 on 2005-12-19
Hi
     I want to install Ubuntu on my pc instead of  Windows xp. If i Format my entire  Hard Disk, would i be able to boot the Ubuntu DVD Disk from CD Drive ? if yes, how ?

---

### Post by cstudent on 2005-12-19
If you have a CD-ROM drive you won't be able to install a DVD disk. If it is a DVD drive then it should be no problem. You don't really need to format the drive either. That can be handled during the Ubuntu install. You will need to make sure that your computer looks to boot from the CD/DVD drive first before it looks to the hard drive. Those settings are set in the BIOS. When your computer boots up you should see a message (sometimes passes by pretty quick) to press a key to enter setup. It varys, but a lot of times it is the del key. Once you have it set to boot from CD you just put the Ubuntu disk in the drive and restart your system. Once the install starts just hit enter and follow the instructions.

---

### Post by skyhigh007 on 2005-12-19
Thank you very much and i have just installed Ubuntu hoary. During the installation, i didnt set up the network and now i want to set up the network. Beofer ubuntu was installed, i have windows installed and was connected to  netGear Router wireless. How can i connect to the net gear router with ubuntu installed using net gear wireless adapator? When i do a browsing network i found its Windows Network.

---

### Post by cstudent on 2005-12-19
If you look under the System menu>Administration>Networking do you see your wireless card and is it active?

---

### Post by skyhigh007 on 2005-12-19
I dont see my wireless card and i only see modem

---

### Post by cstudent on 2005-12-19
Well, obviously you need to get the wireless card recognized by Ubuntu. I don't have one to even experiment with so the best I can do is help you find threads that might have information that pertains to your situation. Take a look at these.

[http://www.ubuntuforums.org/showthread.php?t=103574](http://www.ubuntuforums.org/showthread.php?t=103574)

[https://wiki.ubuntu.com/forum/hardware/ndiswrapper?highlight=%28ndiswrapper%29](https://wiki.ubuntu.com/forum/hardware/ndiswrapper?highlight=%28ndiswrapper%29)

[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

In the mean time I'll try to find someone with more wireless experience offer some advice.

---

### Post by Lambert on 2005-12-19
Skyhigh007,

If you do not see your device in the list when you bring up networking then you do not have a working driver. That probably means the card you have does not have a native linux driver with breezy. So you will have to use ndiswrapper.

Try the links that cstudent gave you to see if you can get wireless working. If not, start a new thread in the networking section of the forums with details about card and your network settings (nothing personal like wep keys are needed) including output of commands from the WTG (not all but just the ones releveant to the section you're stuck at).

If it all seemsm to complicated just start the thread with what card and model# plus output of these commands

sudo lshw -C network

lspci -v

---

### Post by skyhigh007 on 2005-12-21
I have the NetGear MA111 Wireless adaptor and NetGear MR814v2 Wireless Router. I download the Ndiswrapper and put it on the external hard dirve. How do you install Ndiswrapper . what are the some of commands. 


Thanks

---

### Post by cstudent on 2005-12-21
Start with this link. Since you already have ndiswrapper installed, skip down to where it says "Install Window Driver".

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)


Also take a look at these links as well:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/FAQ](http://ndiswrapper.sourceforge.net/mediawiki/index.php/FAQ)
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Troubleshooting](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Troubleshooting)

---

### Post by skyhigh007 on 2005-12-21
lspci -v
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
        Subsystem: Asustek Computer, Inc. A7V133/A7V133-C Mainboard
        Flags: bus master, medium devsel, latency 8
        Memory at e6000000 (32-bit, prefetchable) [size=32M]
        Capabilities: [a0] AGP version 2.0
        Capabilities: [c0] Power Management version 2

0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP] (prog-if 00 [Normal deco de])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: d7000000-d7dfffff
        Prefetchable memory behind bridge: d7f00000-e5ffffff
        Capabilities: [80] Power Management version 2

0000:00:04.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
        Subsystem: Asustek Computer, Inc. A7V133/A7V133-C Mainboard
        Flags: bus master, stepping, medium devsel, latency 0
        Capabilities: [c0] Power Management version 2

0000:00:04.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master  IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Flags: bus master, medium devsel, latency 32
        I/O ports at b800 [size=16]
        Capabilities: [c0] Power Management version 2

0000:00:04.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16) (prog-i f 00 [UHCI])
        Subsystem: VIA Technologies, Inc. (Wrong ID) USB Controller
        Flags: bus master, medium devsel, latency 32, IRQ 9
        I/O ports at b400 [size=32]
        Capabilities: [80] Power Management version 2

0000:00:04.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16) (prog-i f 00 [UHCI])
        Subsystem: VIA Technologies, Inc. (Wrong ID) USB Controller
        Flags: bus master, medium devsel, latency 32, IRQ 9
        I/O ports at b000 [size=32]
        Capabilities: [80] Power Management version 2

0000:00:04.4 Host bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
        Subsystem: Asustek Computer, Inc. A7V133/A7V133-C Mainboard
        Flags: medium devsel, IRQ 9
        Capabilities: [68] Power Management version 2

0000:00:0a.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
        Subsystem: Creative Labs CT4832 SBLive! Value
        Flags: bus master, medium devsel, latency 32, IRQ 9
        I/O ports at 9400 [size=32]
        Capabilities: [dc] Power Management version 1

0000:00:0a.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 08)
        Subsystem: Creative Labs Gameport Joystick
        Flags: bus master, medium devsel, latency 32
        I/O ports at 9000 [size=8]
        Capabilities: [dc] Power Management version 1

0000:00:0d.0 Communication controller: Tiger Jet Network Inc. Tiger3XX Modem/ISDN interface
        Subsystem: Intel Corp.: Unknown device 0003
        Flags: bus master, medium devsel, latency 32, IRQ 9
        I/O ports at 8800 [size=256]
        Memory at d6800000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [40] Power Management version 2

0000:00:11.0 Unknown mass storage controller: Promise Technology, Inc. PDC20265 (FastTrak100 Lite/Ultr a100) (rev 02)
        Subsystem: Promise Technology, Inc. Ultra100
        Flags: bus master, medium devsel, latency 32, IRQ 10
        I/O ports at 8400 [size=8]
        I/O ports at 8000 [size=4]
        I/O ports at 7800 [size=8]
        I/O ports at 7400 [size=4]
        I/O ports at 7000 [size=64]
        Memory at d6000000 (32-bit, non-prefetchable) [size=128K]
        Capabilities: [58] Power Management version 1

0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R100 QD [Radeon 7200] (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc Radeon 7000/Radeon
        Flags: bus master, stepping, 66MHz, medium devsel, latency 64, IRQ 11
        Memory at d8000000 (32-bit, prefetchable) [size=128M]
        I/O ports at d800 [size=256]
        Memory at d7000000 (32-bit, non-prefetchable) [size=512K]
        Expansion ROM at d7fe0000 [disabled] [size=128K]
        Capabilities: [58] AGP version 2.0
        Capabilities: [50] Power Management version 2

---

