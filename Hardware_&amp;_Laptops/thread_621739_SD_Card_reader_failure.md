---
title: "SD Card reader failure"
date: 2007-11-24
forum: Hardware &amp; Laptops
---

### Post by tannedin on 2007-11-24
I have an SD card reader built into my laptop.  Before last night everything worked fine.  IE: the card would be automatically mounted and I could read/write the device.

However, last night I inserted the card and my finger slipped in the process, and the card itself did not click into the slot all the way.  The slot's light remained lit for about 10 seconds and then went out completely, where the norm is high speed flickering for about 3 seconds before an icon shows up on my desktop and in nautilus.
The entier laptop froze: keyboard/mouse and ctrl+alt+bksp to restart gnome.  I waited about 3 minutes before pressing the power button to force the laptop to shut down, where I waited about another minute before brining it back up.

The laptop came up fine except for two things: a.) gnome-setting-daemon did not fire off automatically, however it did work once I had a gnome-terminal and command line started it and b.) the SD card slot appears to not work.  I tried inserting and removing the card 4 or 5 times before I restarted the laptop via gnome to make sure gnome-settings-daemon wasn't broken and could come up on its own.

The second boot worked fine except for the SD problem.

Some techinical data:
Laptop: IBM (lenova) z60m running Ubuntu Gutsy (progression upgrade since Edgy)
SD Cards tested: 1 GB Lexor SD Card and a 1 GB Kodak SD Card

output of "lspci"
```

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM575</1M Gigabit Ethernet PCI Express (rev 11)
14:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
14:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
14:00.2 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
14:00.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
14:02.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

```

I have also attempted the [How_to_get_the_internal_SD-CARD_working]("http://www.thinkwiki.org/wiki/How_to_get_the_internal_SD-CARD_working") fix, but that does not cause either the device to blink in activity or the card to be mounted.

The two SD cards in question work to all expectation in a Palm T|X Handheld and Nikon Camera.

If i was to hazard a guess, its like that expansion slot is not getting power but thats only a guess.

if there is any more data that would make this diagnosis / fix easier, please ask.

---

