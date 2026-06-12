---
title: "No sound after installation on Toughbook CF 51"
date: 2012-12-08
forum: Hardware
---

### Post by ceol on 2012-12-08
Hi you all!

Today I just got my  Toughbook CF-51.  I instantly installed linux (the latest xubuntu) on it, as Im used to do with my computers.

Whatever, this time I have a Problem I wasnt able to solve myself by now. 
The sound does not work. At first, it was just that the internal speakers wouldnt give me any sound, but having a headphone in the front-headphone-jack would, but it was very, very quiet. Then, I searched some stuff on some forums and I finally found this:
[http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)
It didnt work for me, so I decided to compile ALSA new for myself, but that didnt help either. 

At some point, the OS stopped recognizing that the hardware is there at all. In the "Sound"-Menu I see "Keine Karten zur Konfiguration verfügbar" (No cards available for configuration) now, which is kind of weird. Probably I destroyed it, but Im not quite sure how. 

When trying to start alsamixer, I get this message: "Fehler beim Öffen des Mixer-Gerätes: Datei oder Verzeichnis nicht gefunden" (Error at opening the Mixer-Device: File or directory not found).

lspci shows me this:

```

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1d.0 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.7 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 19)
06:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev aa)
06:00.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev aa)
06:00.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 02)
06:04.0 Network controller: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection (rev 05)

```

Sound device should be "00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)", right? 

So the system sees it, and though the module snd-hda-intel is loaded into the kernel, it doesnt recognize it.


I now have no idea left what to do. Trying a live-CD reveals the same problem I had at the beginning: Sound only from front-Jacks, not from the speakers of the laptop itself. 

hwinfo --sound gives me this:

```

> hal.1: read hal dataprocess 3594: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 282.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
18: PCI 1e.2: 0401 Multimedia audio controller                  
  [Created at pci.318]
  Unique ID: r0Vg.+HPOZCxSu0C
  SysFS ID: /devices/pci0000:00/0000:00:1e.2
  SysFS BusID: 0000:00:1e.2
  Hardware Class: sound
  Model: "Intel 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x266e "82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller"
  SubVendor: pci 0x10f7 "Matsushita Electric Industrial Co., Ltd."
  SubDevice: pci 0x8346 
  Revision: 0x04
  Driver: "oss_ich"
  Driver Modules: "oss_ich"
  I/O Ports: 0x1c00-0x1cff (rw)
  I/O Ports: 0x18c0-0x18ff (rw)
  Memory Range: 0xb0040800-0xb00409ff (rw,non-prefetchable)
  Memory Range: 0xb0040400-0xb00404ff (rw,non-prefetchable)
  IRQ: 17 (7333 events)
  Module Alias: "pci:v00008086d0000266Esv000010F7sd00008346bc04sc01i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```


So, does anyone have an idea whats going on with that thing and how to fix it?


Any help is greatly appreciated. ):P

---

