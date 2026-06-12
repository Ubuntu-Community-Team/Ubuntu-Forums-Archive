---
title: "burning with Asus DRW-1608P2S"
date: 2006-01-23
forum: Hardware &amp; Laptops
---

### Post by tcwitte on 2006-01-23
I've recently bought this (IDE) DVD writer (firmware 1.22) and have successfully written a DVD and a CD-RW with it, but too often DVDs fail (3 in a row). I'm using an up-to-date Breezy and Asus K8N mainboard. Details at the bottom.

I've used NeroLINUX and the Nautilus CD/DVD burner. Both report that the disc in question was successfully burned (NeroLINUX even validated the whole DVD!), while only a part (NeroLINUX) or nothing (Nautilus) is on the disc (the disc is closed however). My test file is 4,3 GB which should fit easily.

What I find suspicious is this line in dmesg:
```
hdc: cdrom_pc_intr: The drive appears confused (ireason = 0x01)
```
This line occurs "everywhere" in dmesg and doesn't only appear when the DVD writer is in use or has something in its tray.

I had this message with my old computer (completely different hardware, 4 years old and working well since the early 2.6 kernels) but now with my computer as well. And DMA wasn't turned on for /dev/hdc (the DVD writer) so I did that by hand because NeroLINUX told me so and made my successful DVD afterwards.

There's nothing in my logs (including .xsession-errors) and the programs report a successful burning, so I don't know where to start.. Thanks in advance for any help.

For a global idea, this is my hardware:

```
taco@cambyses:/var/log $ lspci -i /usr/share/hwdata/pci.ids
0000:00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
0000:00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
0000:00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
0000:00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
0000:00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
0000:00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2)
0000:00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)
0000:00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2)
0000:00:0a.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev a2)
0000:00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2)
0000:00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)
0000:01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (Secondary) (rev 01)
0000:02:07.0 Multimedia controller: Philips Semiconductors SAA713X Audio+video broadcast decoder (rev d0)
0000:02:09.0 Multimedia audio controller: Creative Labs SB Audigy LS
```

---

### Post by tcwitte on 2006-01-28
Now I've seen this as well while writing a DVD+RW (my burner supports all formats):

> hdc: write_intr: bad interrupt reason 1
hdc: status error: status=0x58 { DriveReady SeekComplete DataRequest }
ide: failed opcode was: unknown
hdc: drive not ready for command
hdc: status error: status=0x50 { DriveReady SeekComplete }
ide: failed opcode was: unknown
hdc: status error: status=0x50 { DriveReady SeekComplete }
ide: failed opcode was: unknown
hdc: status error: status=0x50 { DriveReady SeekComplete }
ide: failed opcode was: unknown
hdc: ATAPI reset complete

---

### Post by tcwitte on 2006-01-29
OK, this works in Dapper.. No such strange kernel messages and the DVDs are good. I've had one failure in Dapper when burning a large file (4.3GB) at maximum speed but I don't know yet what caused the problem.

---

