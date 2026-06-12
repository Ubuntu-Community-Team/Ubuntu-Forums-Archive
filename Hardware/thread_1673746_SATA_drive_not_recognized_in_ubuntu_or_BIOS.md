---
title: "SATA drive not recognized in ubuntu or BIOS"
date: 2011-01-22
forum: Hardware
---

### Post by fms714 on 2011-01-22
I'm trying to install a second hard drive to dual boot windows and ubuntu, but i can't get it to be recognized anywhere. I've checked the wiring multile times and used different ports and SATA cables, but nothing works. I alredy have a drive working fine with ubuntu on it, but can't get this one to work. It would be great if anyone could help with this problem.

---

### Post by fms714 on 2011-01-22
Anything at all would really help. Is the drive broken?

---

### Post by cascade9 on 2011-01-23
If you cant see the drive in BIOS, then it probably is broken. 

You could try the freezer trick. ;)

---

### Post by aileen on 2011-01-23
A new drive, so badly broken it's not recognized in BIOS? Never heard of that...i've seen..eh..heard, hard drives sound like an angle grinder, but it showed up just fine in BIOS! :p 

If your sata controller isn't of the latest model (like mine), i think you'll  have to set the drive to sata1 mode (max 1.5gbit instead of max 3 gbit if i remember correctly), with a small jumper or it won't be recognized at all. Start with checking if your controller supports sata2, and if there's a jumper on the drive.

---

### Post by cascade9 on 2011-01-23
Who said anything about 'new'?

---

### Post by fms714 on 2011-01-23
It is new. Thanks for the advice. I'm not trying to recover any data, looking for a permanent fix if there is one, so the freezer trick wouldn't be too practical. I should have been more specific in the original post. I have a warranty, so if needed, I can always get a new one.

---

### Post by amsterdamharu on 2011-01-24
Have you checked BIOS settings for the sata controllers?
As asked before did you check the jumpers on the harddisk?

Did you connect the drive to this controller:
SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] (rev 40)
or this one:
SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02)

(got the lspci from another thread.)

---

### Post by cascade9 on 2011-01-24
> **amsterdamharu said:**
> Have you checked BIOS settings for the sata controllers?
As asked before did you check the jumpers on the harddisk?

Did you connect the drive to this controller:
SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] (rev 40)
or this one:
SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02)

(got the lspci from another thread.)

Nicely done. 

'IDE mode' is probably your problem. Try using the SB700/800 ports (should be 4-6 of them), with the controller in AHCI mode, not IDE mode.

---

### Post by fms714 on 2011-01-24
Thanks for that, Ill try the other controller today.

---

### Post by fms714 on 2011-01-24
I changed the settings, but I can't see any results. I havn't tried the windows setup yet because i dont have time tonight, but I'll try it tomorrow. Heres the updated lspci
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
    Subsystem: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
    Kernel modules: shpchp
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] (rev 40)
    Subsystem: Giga-byte Technology Device b002
    Kernel driver in use: ahci
    Kernel modules: ahci
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
    Subsystem: Giga-byte Technology Device 5004
    Kernel driver in use: ohci_hcd
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
    Subsystem: Giga-byte Technology Device 5004
    Kernel driver in use: ehci_hcd
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
    Subsystem: Giga-byte Technology Device 5004
    Kernel driver in use: ohci_hcd
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
    Subsystem: Giga-byte Technology Device 5004
    Kernel driver in use: ehci_hcd
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
    Kernel modules: i2c-piix4
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
    Subsystem: Giga-byte Technology Device a102
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
    Subsystem: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
    Subsystem: Giga-byte Technology Device 5004
    Kernel driver in use: ohci_hcd
00:15.0 PCI bridge: ATI Technologies Inc Device 43a0
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
    Subsystem: Giga-byte Technology Device 5004
    Kernel driver in use: ohci_hcd
00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
    Subsystem: Giga-byte Technology Device 5004
    Kernel driver in use: ehci_hcd
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
    Kernel modules: amd64_edac_mod
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
    Kernel driver in use: k10temp
    Kernel modules: k10temp
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4290]
    Subsystem: Giga-byte Technology Device d000
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
    Subsystem: Giga-byte Technology Device 960f
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
02:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
    Subsystem: Giga-byte Technology Device 5007
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci-hcd
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
    Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
    Kernel driver in use: r8169
    Kernel modules: r8169
04:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
    Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci, ohci1394
05:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02)
    Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
    Kernel driver in use: ahci
    Kernel modules: ahci
05:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02)
    Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
    Kernel driver in use: pata_jmicron
    Kernel modules: pata_jmicron
frank@frank-GA-890GPA-UD3H:~$ 

```

---

### Post by cascade9 on 2011-01-25
If its WinXP, using AHCI means that it wont boot (you'd need to load the drivers via a floppy disc during the install of XP for it to be able to use AHCI). 

Still nothing......is the disc even spinning up? (you can normally tell from sound or feel if the drive is spinning up). What model HDD is it anyway?

---

### Post by fms714 on 2011-01-25
Im going to use it with windows 7, so i should be able to use a usb flash drive for the drivers. I have them on a disk. Its a western digital Caviar green WD10EADS. Its a second drive, so its hard to tell by sound but ill open up the case to check if its spinning today.

---

### Post by Yellow Pasque on 2011-01-25
Is it still not recognized in the BIOS, even after trying different SATA ports? If so, it's likely a DOA drive (it happens). Double-check that both the power and data cables are firmly connected and maybe try a different SATA data cable if you have one handy.

---

### Post by fms714 on 2011-01-26
It still doesnt work with the drivers, I've tried all of the sata cables and ports I have, and I've re-tried everything multiple times. I think I'll just return it on warranty, get another one, and try that.

---

### Post by cascade9 on 2011-01-27
Probably DOA then. 

I'm running the same type drive on the same AMD SB7XX/8XX controller, no issues (worked in IDE mode as well BTW, not that you should use IDE mode without a good reason)

---

