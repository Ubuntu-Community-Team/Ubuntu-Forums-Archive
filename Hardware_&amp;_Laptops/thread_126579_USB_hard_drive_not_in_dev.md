---
title: "USB hard drive not in /dev"
date: 2006-02-06
forum: Hardware &amp; Laptops
---

### Post by ScarletEmerald on 2006-02-06
Hi, I'm having some trouble accessing my external USB hard drive.  It's an (old) Buslink 60GB USB 1 drive formatted with FAT32.  According to dmesg it's being detected when I plug it in, but it doesn't seem to be putting an sd* file in /dev (I have sda, sdb, and sdc, but these correspond to my three SATA hard drives).

The drive works fine when I boot to windows, so I don't think it's a hardware problem.

I read that someone solved a similar problem by doing *modprobe --remove ehci-hcd* so I gave that a try, but it didn't seem to have any effect.

Here's my *dmseg | tail* output after I unplugged it and plugged it back in
```
[4294722.817000] Bluetooth: RFCOMM TTY layer initialized
[4294726.851000] eth0: no IPv6 routers present
[4313140.451000] ehci_hcd 0000:00:02.2: remove, state 1
[4313140.451000] usb usb3: USB disconnect, address 1
[4313140.455000] ehci_hcd 0000:00:02.2: USB bus 3 deregistered
[4313140.488000] ACPI: PCI interrupt for device 0000:00:02.2 disabled
[4313403.265000] usb 2-3: USB disconnect, address 3
[4313407.942000] usb 2-3: new full speed USB device using ohci_hcd and address 4
[4313453.265000] usb 2-3: USB disconnect, address 4
[4313459.692000] usb 2-3: new full speed USB device using ohci_hcd and address 5
```

Can anyone give me some tips on how to troubleshoot this?

---

### Post by wondering_jew on 2006-02-06
have you tried the disk manager  (system-->administration-->Disks) it should probably show up there and it will tell you the access path and all that too.

---

### Post by ScarletEmerald on 2006-02-06
[QUOTE=wondering_jew]have you tried the disk manager  (system-->administration-->Disks) it should probably show up there and it will tell you the access path and all that too.[/QUOTE]
I took a look, but it's not showing up in the disk manager.

---

### Post by devnulljp on 2006-02-06
Try lsusb to see the state of your usb, then sudo modprobe -r ehci_hcd (underscore not a hyphen), then lsusb again and see if anything's changed.
See what pops up in mesg after the modprobe.

---

### Post by jeluranni on 2006-02-06
I'm having the same problem. My USB drive is not showing up in media when inserted. The disk manager shows that the drive is recognized and is there. No access path is given.

---

### Post by jeluranni on 2006-02-07
Update - I got it to work.

I did a mkdir /media/usbdrive and then used the disk manager to point the access path to media/usbdrive.

Everything works now. The drive shows up in the places menu and in computer. I'm a little puzzled that a mount point wasn't created automatically.

---

### Post by ScarletEmerald on 2006-02-07
[QUOTE=devnulljp]Try lsusb to see the state of your usb, then sudo modprobe -r ehci_hcd (underscore not a hyphen), then lsusb again and see if anything's changed.
See what pops up in mesg after the modprobe.[/QUOTE]
lsusb seems to show the drive (I think it's the bus 002 device 008 ), but the modprobe didn't change much- just killed the bus 003.

lsusb before modprobe
```
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 008: ID 067b:2307 Prolific Technology, Inc. PL2307 USB-ATAPI4 Bridge
Bus 002 Device 006: ID 0764:0005 Cyber Power System, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 046d:c00e Logitech, Inc. Optical Mouse
Bus 001 Device 001: ID 0000:0000

```

lsusb after modprobe
```
Bus 002 Device 008: ID 067b:2307 Prolific Technology, Inc. PL2307 USB-ATAPI4 Bridge
Bus 002 Device 006: ID 0764:0005 Cyber Power System, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 046d:c00e Logitech, Inc. Optical Mouse
Bus 001 Device 001: ID 0000:0000

```

dmesg
```
[4345946.984000] ehci_hcd 0000:00:02.2: remove, state 1
[4345946.984000] usb usb3: USB disconnect, address 1
[4345946.987000] ehci_hcd 0000:00:02.2: USB bus 3 deregistered
[4345946.989000] ACPI: PCI interrupt for device 0000:00:02.2 disabled

```

Still no entry in /dev or disk manager.

---

### Post by ScarletEmerald on 2006-02-09
Can anyone tell me what chain of events is supposed to happen between the drive being detected as a new USB device and an entry being placed in /dev ?  Maybe I can try to trace this through and see where the problem is occurring.

---

### Post by ScarletEmerald on 2006-02-11
Ok, I recently found [this webpage]("http://bravin.home.cern.ch/bravin/usbide/usbide.html") which is a little discouraging... this guy apparently wrote a "Linux Device Driver" to get his Buslink USB drive to work, but says he won't be updating it for the 2.6 kernel.   Does anyone know if some kind of equivalent functionality is built into the kernel now or available elsewhere, or am I SOL?

---

### Post by ScarletEmerald on 2006-02-11
For anyone who was curious about this, it seems that there is no way to use this particular Buslink USB drive with the 2.6.x kernel.  Apparently in my /proc/bus/usb/devices

```
T:  Bus=02 Lev=01 Prnt=01 Port=02 Cnt=02 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=067b ProdID=2307 Rev= 2.01
S:  Manufacturer=Buslink
S:  Product=BUSlink USB-IDE Bridge Controller
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=01(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=82(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=83(I) Atr=03(Int.) MxPS=   7 Ivl=1ms
I:  If#= 0 Alt= 1 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=01(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=82(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
```

the "Cls=ff(vend.)" means the drive is using a vendor specific protocol for which there is no built-in driver, hence the "Driver=(none)".  After taking a look at [this post]("http://sourceforge.net/mailarchive/message.php?msg_id=9461421"), it looks like I really am SOL...

---

