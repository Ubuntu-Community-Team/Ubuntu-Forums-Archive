---
title: "Max resolution too low for dual monitors"
date: 2014-02-07
forum: Hardware
---

### Post by jeremy11 on 2014-02-07
So I just installed Linux for the first time to give it a try, and while I did manage to install my HD 5450 plus having fixed most major bugs already, I really can't find out what's up with my graphic card.
Basically, I got my 2 monitors; 1 through VGA with a resolution of 1680x1050, and the other running from HDMI to DVI on a resolution of 1280x1024.
Now, when I try to adjust the settings so that both of my monitors show their best, Ubuntu keeps giving me the message that my max supported resolution will be 1680 by 1680, and the resolutions of both monitors apparently count up.
The deal is, in Windows it always worked, so it's not the hardware.
Could I maybe have screwed up installing the graphic card?

Thanks in advance!
-Jeremy

ps: don't mind my stone-age hardware and monitors, this is just temporary

---

### Post by jp734 on 2014-02-08
execute the following on terminal and post results

xrandr
lspci -k  (look for your video card as this will show all devices on your system)

have you installed the fglrx driver?

---

### Post by jeremy11 on 2014-02-08
When typing in lspci -k this is the information it gives me:

00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
    Subsystem: Micro-Star International Co., Ltd. Device 7653
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
    Subsystem: Micro-Star International Co., Ltd. Device 7653
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 01)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 01)
    Subsystem: Micro-Star International Co., Ltd. Device 7653
    Kernel driver in use: uhci_hcd
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 01)
    Subsystem: Micro-Star International Co., Ltd. Device 7653
    Kernel driver in use: uhci_hcd
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01)
    Subsystem: Micro-Star International Co., Ltd. Device 7653
    Kernel driver in use: uhci_hcd
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 01)
    Subsystem: Micro-Star International Co., Ltd. Device 7653
    Kernel driver in use: uhci_hcd
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 01)
    Subsystem: Micro-Star International Co., Ltd. Device 7653
    Kernel driver in use: ehci-pci
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
    Subsystem: Micro-Star International Co., Ltd. Device 7653
    Kernel driver in use: lpc_ich
    Kernel modules: leds-ss4200, lpc_ich, intel-rng
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
    Subsystem: Micro-Star International Co., Ltd. Device 7653
    Kernel driver in use: ata_piix
    Kernel modules: pata_acpi
00:1f.2 IDE interface: Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 01)
    Subsystem: Micro-Star International Co., Ltd. Device 7653
    Kernel driver in use: ata_piix
    Kernel modules: pata_acpi
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 01)
    Subsystem: Micro-Star International Co., Ltd. Device 7653
    Kernel modules: i2c-i801
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cedar [Radeon HD 5000/6000/7350/8350 Series]
    Subsystem: Micro-Star International Co., Ltd. Device 2121
    Kernel modules: radeon
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cedar HDMI Audio [Radeon HD 5400/6300 Series]
    Subsystem: Micro-Star International Co., Ltd. Device aa68
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 03)
    Subsystem: Micro-Star International Co., Ltd. Device 7653
    Kernel driver in use: r8169
    Kernel modules: r8169

And I can remember something about not finding the right fglrx driver and I stopped trying downloading it from there.

edit: I'm 99% sure the problem is with the driver, however I can't seem to install it correctly somehow

---

### Post by jp734 on 2014-02-08
what did xrandr give you? 

I currently am using fglrx driver and I use Catalyst to configure my monitor setup. Not sure about radeon. Might have to use configuration files. Did you try using **synaptic package manager** to install fglrx? If not, try that. It's what Im using right now with my HD5450 as well. After installing, run amdconfig --initial, reboot and then start catalyst. 

**But try xrandr first, recommended by everyone.**

---

