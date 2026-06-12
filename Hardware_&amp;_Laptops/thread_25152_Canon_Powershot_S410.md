---
title: "Canon Powershot S410"
date: 2005-04-09
forum: Hardware &amp; Laptops
---

### Post by fizzatbeyond on 2005-04-09
](*,) For the life of me I can't get my wife's camera to work (Canon S410),  I know it's supported by libgphoto2, and I can get it to work on my laptop (which is debian SID), but for some reason I cannot get it to work on her computer which is running Hoary.  

I did have it working on on Warty at one point (well before the upgrade).  Going throught the docs the only thing I came up with is that it wants /proc/bus/usb to be mounted which for some reason it's not on this box but is on mine.

When I try to mount it, it tells me 'unknown filesystem type usbdevfs'.  Any suggestions?

---

### Post by kleeman on 2005-04-09
Couple of suggestions:
I had better luck with my powershot with digikam (its in the universe repository).
What does dmesg give when you plug in the usb connector?

---

### Post by fizzatbeyond on 2005-04-11
The extent of what dmesg gives me is as follows:

usb 1-1: new full speed USB device using uhci_hcd and address 4

The error gthumb gives me is this:
[COLOR=Red]An error occurred in the io-library ('Bad parameters'): Could not find USB device (vendor 0x4a9, product 0x30ba). Make sure this device is connected to the computer.
[/COLOR]
which makes me think something is screwed up.

As for digikam (which is what I use on my laptop), gives me basicly the same results as gthumb and the commandline interface as gphoto2.

Any more ideas?

---

### Post by kleeman on 2005-04-11
Hmm thats what I get (the dmesg stuff anyway). What does lsusb show after plugging the camera in? Also what does gphoto2 --list-ports show? and finally are your permissions set for /proc/bus/usb ( ls -Rl /proc/bus/usb shows?) This page has a lot of (dated) info:

[http://www.gphoto.org/doc/manual/permissions-usb.html](http://www.gphoto.org/doc/manual/permissions-usb.html)

---

### Post by fizzatbeyond on 2005-04-12
[QUOTE=kleeman]Hmm thats what I get (the dmesg stuff anyway). What does lsusb show after plugging the camera in?[/QUOTE]

shanna@pez:/proc/bus $ lsusb
shanna@pez:/proc/bus $

[QUOTE=kleeman] Also what does gphoto2 --list-ports show? [/QUOTE]

Devices found: 34
Path                             Description
--------------------------------------------------------------
usb:                             Universal Serial Bus
(I cut out all the serial ports because the camera is usb)

[QUOTE=kleeman]and finally are your permissions set for /proc/bus/usb ( ls -Rl /proc/bus/usb shows?) This page has a lot of (dated) info:[/QUOTE]

shanna@pez:/proc/bus $ ls -lR usb
usb:
total 0

All this brings me back to my original thought that /proc/bus/usb should be mounted but is not and when I try to mount it by hand it tells me:
mount: unknown filesystem type 'usbdevfs'

---

### Post by kleeman on 2005-04-12
I think you have some very serious problems with usb! Here is what lsusb shows for me:

Bus 005 Device 004: ID 04b8:011e Seiko Epson Corp. Perfection 1660 Photo
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 002: ID 03f0:3e02 Hewlett-Packard
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 046d:c03e Logitech, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

and  gphoto2 --list-ports
usb:                             Universal Serial Bus
usb:005,004                      Universal Serial Bus
usb:004,002                      Universal Serial Bus
usb:002,003                      Universal Serial Bus




and finally: 
 ls -lR /proc/bus/usb
/proc/bus/usb:
total 0
dr-xr-xr-x    1 root     root            0 Apr 11 23:20 001
dr-xr-xr-x    1 root     root            0 Apr 11 23:20 002
-r--r--r--    1 root     root            0 Apr 11 23:20 devices
-r--r--r--    1 root     root            0 Apr 11 23:20 drivers

/proc/bus/usb/001:
total 1
-rw-r--r--    1 root     root           18 Apr 11 23:20 001

/proc/bus/usb/002:
total 1
-rw-r--r--    1 root     root           18 Apr 11 23:20 001

So does dmesg show any usb detection on your system during bootup? Mine has:

usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
uhci_hcd 0000:00:1d.0: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI
#1
PCI: Setting latency timer of device 0000:00:1d.0 to 64
uhci_hcd 0000:00:1d.0: irq 23, io base 0xcc00
uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
uhci_hcd 0000:00:1d.1: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI
#2
PCI: Setting latency timer of device 0000:00:1d.1 to 64
uhci_hcd 0000:00:1d.1: irq 19, io base 0xd000
uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
uhci_hcd 0000:00:1d.2: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI
#3
PCI: Setting latency timer of device 0000:00:1d.2 to 64
uhci_hcd 0000:00:1d.2: irq 18, io base 0xd400
uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
ACPI: PCI interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
uhci_hcd 0000:00:1d.3: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI
#4
PCI: Setting latency timer of device 0000:00:1d.3 to 64
uhci_hcd 0000:00:1d.3: irq 16, io base 0xd800
uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 2 ports detected
usb 2-1: new low speed USB device using uhci_hcd and address 2
ACPI: PCI interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
ehci_hcd 0000:00:1d.7: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI
 Controller
PCI: Setting latency timer of device 0000:00:1d.7 to 64
ehci_hcd 0000:00:1d.7: irq 23, pci mem 0xfebff800
ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
PCI: cache line size of 128 is not supported by device 0000:00:1d.7
ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
hub 5-0:1.0: USB hub found
hub 5-0:1.0: 8 ports detected
usbcore: registered new driver hiddev
usb 2-1: USB disconnect, address 2
hw_random hardware driver 1.0.0 loaded
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
usb 5-8: new high speed USB device using ehci_hcd and address 4
ACPI: PCI interrupt 0000:06:03.0[A] -> GSI 19 (level, low) -> IRQ 19
usb 2-1: new low speed USB device using uhci_hcd and address 3
input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.1
-1
gameport: pci0000:06:03.1 speed 710 kHz
ts: Compaq touchscreen protocol output
usb 4-1: new full speed USB device using uhci_hcd and address 2
ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
ACPI: PCI interrupt 0000:06:03.2[B] -> GSI 18 (level, low) -> IRQ 18
ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[feafb800-feafbfff]  Max
 Packet=[2048]
ACPI: PCI interrupt 0000:06:05.0[A] -> GSI 17 (level, low) -> IRQ 17
ohci1394: fw-host1: Unexpected PCI resource length of 1000!
ohci1394: fw-host1: OHCI-1394 1.0 (PCI): IRQ=[17]  MMIO=[feafa000-feafa7ff]  Max
 Packet=[2048]
drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 1 pr
oto 2 vid 0x03F0 pid 0x3E02
usbcore: registered new driver usblp
drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver

---

### Post by fizzatbeyond on 2005-04-13
[QUOTE=kleeman]Hmm thats what I get (the dmesg stuff anyway). What does lsusb show after plugging the camera in? Also what does gphoto2 --list-ports show? and finally are your permissions set for /proc/bus/usb ( ls -Rl /proc/bus/usb shows?) This page has a lot of (dated) info:

[http://www.gphoto.org/doc/manual/permissions-usb.html](http://www.gphoto.org/doc/manual/permissions-usb.html)[/QUOTE]

When I do a dmesg I don't really get much usb stuff showing up...

usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 5
PCI: setting IRQ 5 as level-triggered
ACPI: PCI interrupt 0000:00:07.2[D] -> GSI 5 (level, low) -> IRQ 5
uhci_hcd 0000:00:07.2: Intel Corp. 82371AB/EB/MB PIIX4 USB
uhci_hcd 0000:00:07.2: irq 5, io base 0x1060
uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
ACPI: PCI interrupt 0000:00:08.0[A] -> GSI 5 (level, low) -> IRQ 5
es1968: clocking to 48000
ohci_hcd: 2004 Nov 08 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)

I also noticed that durring bootup it complains that the mount point for /proc/bus/usb does not exist.  That along with the fact that the filesystem type (usbdevfs) does not exist inside of my kernel. (when I cat /proc/filesystems it is not listed) made me guess that the kernel was not compiled with usbdevfs, however looking in the config in /boot tells me that it was.

I'm running out of straws to grab here.  Could it have ANYTHING to do with the fact that / is reiserfs (I can't stand ext3 just because it feels like such a hack).  

If you don't have any more ideas I guess I'll compile my own kernel (which I normaly do for my machines but didn't want to do on my wife's computer).  Then I can be sure that the problem is fixed (and it'll get rid of the boot error that always comes up about / not being ext3)

---

### Post by kleeman on 2005-04-13
All that sounds fairly serious. It sounds like something very basic is going wrong with the usb system. IMHO I would doubt that reiserfs was the issue and the standard ubuntu kernel should be fine. I looked at the linux usb howto and it did mention one other thing: is usb disabled in the bios by any chance? Anyway sorry I can't help much here is the howto:

 [http://www.linux-usb.org/USB-guide/p13.html](http://www.linux-usb.org/USB-guide/p13.html)

---

### Post by fizzatbeyond on 2005-04-14
[QUOTE=kleeman]All that sounds fairly serious. It sounds like something very basic is going wrong with the usb system. IMHO I would doubt that reiserfs was the issue and the standard ubuntu kernel should be fine. I looked at the linux usb howto and it did mention one other thing: is usb disabled in the bios by any chance? Anyway sorry I can't help much here is the howto:

 [http://www.linux-usb.org/USB-guide/p13.html](http://www.linux-usb.org/USB-guide/p13.html)[/QUOTE]

See I don't think it is that serious for two reasons.
1)  It worked properly under warty before I upgraded it.
2)  Some usb things still work (aka the usb mouse that I am currently using).  which by the way does not us /proc it uses /dev.

Oh well If I can't figure it out by this weekend I'll re-install it with debian (which I an much more familiar with)

Thanks for your help.

Well looks like I spoke too soon.  After a little bit more putzing (don't know why I didn't think of this earlier)  I commented out the /proc/bus/usb line from /etc/fstab and rebooted and low and behold I now have stuff in that dir and lsusb works AND even better then that I can now get the camera to work.  Crazy thing.  ah well whatever.

Again thanks for all your help.

---

### Post by kleeman on 2005-04-14
Fair enough and well done. I think however that there is a bug somewhere in usb hoary that deserves perhaps reporting.

---

### Post by M.A.X on 2005-08-03
I was getting the same problem with gphoto2.

When I was doing a lsusb in a user' terminal, I couldn't see my camera but I could see my USB mouse :
```
maxence@portable-max:~$ lsusb
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 1241:1166 Belkin (?)
Bus 001 Device 001: ID 0000:0000
``` 

but in a superuser (root) terminal :
```
root@portable-max:/home/maxence # lsusb
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 005: ID 040a:0111 Kodak Co. DC-265
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 1241:1166 Belkin (?)
Bus 001 Device 001: ID 0000:0000
``` 

So, it seems to be a permission problem. I've take a look to /etc/hotplug/usb/libgphoto2 and I have seen "GROUP=plugdev".
So I've just done a 
```
 root@portable-max:/home/maxence # useradd maxence plugdev
``` 
Close the session (to take into account the new group) and everything is now working fine  :razz:
```
 
maxence@portable-max:~$ groups
users audio video plugdev
maxence@portable-max:~$ lsusb
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 006: ID 040a:0111 Kodak Co. DC-265
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 1241:1166 Belkin (?)
Bus 001 Device 001: ID 0000:0000

```

---

