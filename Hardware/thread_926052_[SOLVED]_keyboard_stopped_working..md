---
title: "[SOLVED] keyboard stopped working."
date: 2008-09-21
forum: Hardware
---

### Post by tacticalbread on 2008-09-21
I was attempting to play Regnum online on my laptop, but the game didn't like my video drivers, so all that was displayed was a bunch of boxes. I couldn't find any exit buttons, so I pushed the power button to shut it down. When I turned it back on my keyboard wasn't working. It won't work anywhere, not even to get into the BIOS settings. The only thing I can actually get into is my Ubuntu live CD.

is this a hardware problem, or can I fix it?

---

### Post by Crafty Kisses on 2008-09-21
I'd like to see the results of this command:
```
lspci
```

---

### Post by nowshining on 2008-09-21
u could of just pushed ctrl+alt+backspace to quickly exit - force exit and re-login..

---

### Post by tacticalbread on 2008-09-21
> **Codename said:**
> I'd like to see the results of this command:
```
lspci
```

I can't type. I can't even log in.

---

### Post by nowshining on 2008-09-21
login to to the livecd and mount via terminal the disk ie:

sudo mkdir /media/harddrive

sudo mount /dev/sda1 /media/harddrive -t ext3

does it mount fine?

then run the last command but change mount to umount...

you may have to manually run fsck on it....  you can try fsck /dev/sda1

---

### Post by tacticalbread on 2008-09-21
well, you know, I would try that, but my keyboard doesn't work, so therefore I can't actually type anything.

and the only keyboard I have is a PS/2 keyboard, and my laptop doesn't a PS/2 port on it.

I'm typing this all from my PSP in case you were wondering.

---

### Post by nowshining on 2008-09-22
so ur keyboard doesnt' work even on the LiveCD?? then it's hardware related and not software related..

---

### Post by tacticalbread on 2008-09-22
I'm at my college using one of the USB keyboards from the library. Mine's still not working at all. In fact, the only buttons on my laptop that work are the power button, and the button that locks the touchpad, although the touchpad doesn't work.

> **Codename said:**
> I'd like to see the results of this command:
```
lspci
```
```
lspci
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
01:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
```

---

### Post by tacticalbread on 2008-09-23
still not working. anyone have any idea why?

---

### Post by lisati on 2008-09-23
Sounds like a hardware problem. If it was a USB keyboard that worked for a short while but then stopped, I'd suggest [this thread]("http://ubuntuforums.org/showthread.php?t=854684")

---

### Post by tacticalbread on 2008-09-23
it was my laptop keyboard, and it was working perfectly fine right before this happened. and, the laptop isn't more than six months old.

---

### Post by tacticalbread on 2008-09-24
well, I fixed it. All I need was a BIOS update.

---

### Post by lisati on 2008-09-24
> **tacticalbread said:**
> well, I fixed it. All I need was a BIOS update.
Whew, that's a relief. Good to hear that things are looking better.

---

### Post by Chibi-Tatsu on 2008-10-20
Anyone know if there's a way without flashing the bios?  I'm seriously paranoid about doing so...

---

### Post by tacticalbread on 2008-10-20
> **Chibi-Tatsu said:**
> Anyone know if there's a way without flashing the bios?  I'm seriously paranoid about doing so...

considering that's the only thing that worked after trying everything else, I doubt it.

---

### Post by Chibi-Tatsu on 2008-11-24
Curiously, after a couple weeks of a workaround involving having an external usb keyboard hooked in from boot-up (and then, when it freezes, unplugging and plugging it back in... voila! internal keyboard and touchpad work just fine), it went back to normal.

I'm not really sure what caused it to break OR to resume normal functioning, but there you go...

---

