---
title: "&quot;packet command error&quot; with DVD-ROM on laptop"
date: 2006-08-31
forum: Hardware &amp; Laptops
---

### Post by Dittohead on 2006-08-31
Hi all.

I got Ubuntu on my old Inspiron 8200, as Windows was acting very poorly on it. After a few configuration changes the random lock ups, the hibernation and suspend issues as well as general slowness for the most disappeared after installing Dapper on it. Much, much better experience.

Anyway I've been having a few issues with my DVD-ROM Drive. If I put a disc in about 80% of the time it'll read it for a few seconds and spit it back out. If it stays it either won't mount or won't find anything on the disc. Every great once in a while it'll actually find the disc and mount it and the data is readable and can copy off just fine.

Here's what [FONT="monospace"]dmesg[/FONT] had to say:

```
[17183488.708000] hdb: packet command error: status=0x51 { DriveReady SeekComplete Error }
[17183488.708000] hdb: packet command error: error=0x51 { IllegalLengthIndication LastFailedSense=0x05 }
[17183488.708000] ide: failed opcode was: unknown
[17183488.708000] cdrom: open failed.
```

[FONT="monospace"]/var/log/messages[/FONT] spits out the same angry vitriol. :P

[FONT="monospace"]lspci[/FONT] output:

```
$ lspci
0000:00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
0000:00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
0000:00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #3) (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
0000:00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
0000:00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go] (rev a3)
0000:02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
0000:02:01.0 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
0000:02:01.1 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
0000:02:01.2 FireWire (IEEE 1394): Texas Instruments PCI4451 IEEE-1394 Controller
0000:02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)
```

Gnome Disks Manager says that the drive is a Samsung CD-RW/DVD-Rom SN-324B device file is [FONT="monospace"]/dev/hdb[/FONT].

Laptop is a Dell Inspiron 8200, Mobile Intel Pentium 4 - M CPU 1.80GHz with a brookdale chipset as mentioned in [FONT="monospace"]lspci[/FONT].

Is my drive just on it's way out? The discs read fine in other computers. Thanks for any ideas.

---

