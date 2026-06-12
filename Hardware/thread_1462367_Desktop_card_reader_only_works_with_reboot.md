---
title: "Desktop card reader only works with reboot"
date: 2010-04-25
forum: Hardware
---

### Post by kempy1000 on 2010-04-25
Hi,

I have just installed a desktop 5 in 1 card reader with a firewire and a usb port in it. The only way to access an SD card is to put the card in and reboot.

Anyone any ideas to as why this is?

This posts solution did not work for me:
[http://ubuntuforums.org/showthread.php?t=1446267](http://ubuntuforums.org/showthread.php?t=1446267)

```

chris@chimera:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 10df:0500 In-Win Development, Inc. iAPP CR-e500 Card reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
```

chris@chimera:~$ lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
01:01.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
01:01.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
01:01.4 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)
02:00.0 Mass storage controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 19)
05:00.0 VGA compatible controller: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series]
05:00.1 Display controller: ATI Technologies Inc RV516 [Radeon X1300 Pro] (Secondary)

```

Thanks :)

---

### Post by garyedwardjohnston on 2010-04-25
not really sure but it seems like an auto mount issue

---

### Post by Neobuntu on 2011-02-08
I think this is because multi card readers need to be unplugged; from their main USB input connection.

I have an external, multi card reader and I have to unplug  the USB cable (and plug it back in) that connects the unit (not just the card) to get it to recycle.

Problem is, my new desktop has a multi reader built-in (to the bay) and I would have to unhook desktop cables, open the case and internally unplug the multi-readers USB cable and then plug it back-in, to get it to work (for the second time used; without a reboot.)

There must be some way to reset the USB manually. Maybe remove and reinstall a certain module or something. Hopefully a GUI app that will assist this, or at least a script.

Anyone? I don't want to mess up auto mount; so what's the best way to regain built-in reader function, without rebooting?

Add:
This works OK when you just yank-out the card and put it back-in. However, when you use "Safely remove", the reader is turned of and **requires** re-plugging. Therefore, we need a re-spawn button or something, because rebooting; to (safely) use a built-in card reader, is unacceptable.

---

### Post by caradeporra on 2011-12-19
Has anyone any info on this?  I have this same issue.  Is there at least a command to restart just the built in card reader so a complete reboot is not required?

Carade

---

