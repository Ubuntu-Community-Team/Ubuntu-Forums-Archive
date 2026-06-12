---
title: "Can anyone help me with my USB printer?"
date: 2005-04-09
forum: Hardware &amp; Laptops
---

### Post by PhilD on 2005-04-09
I am having problems with my printer - actually I think it is the auto-detection of my USB hubs which isn't working correctly. My computer is a home-built and I have always had trouble getting with the USB under MS Windows, I can't get all the ports to work. However, my printer DOES work under Windows, but not under Ubuntu.

Hardware:
HP Deskjet 895CXi connected to a USB port (heaven knows which one!)

USB mouse which works fine under Ubuntu.

Motherboard is an nForce2 job:
[http://www.msicomputer.com/product/detail_spec/product_detail.asp?model=K7N2G-ILSR](http://www.msicomputer.com/product/detail_spec/product_detail.asp?model=K7N2G-ILSR)

Here are the messges from bootup, any help would be much appreciated!


```
PCI: Enabling device 0000:01:0b.0 (0000 -> 0003)
ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
ACPI: PCI interrupt 0000:01:0b.0[A] -> GSI 18 (level, high) -> IRQ 18
ata1: SATA max UDMA/133 cmd 0xF8B4C200 ctl 0xF8B4C238 bmdma 0x0 irq 18
ata2: SATA max UDMA/133 cmd 0xF8B4C280 ctl 0xF8B4C2B8 bmdma 0x0 irq 18
eth0: link up.
ata1: no device found (phy stat ffffffff)
scsi0 : sata_promise
ata2: no device found (phy stat ffffffff)
scsi1 : sata_promise
hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
ohci1394: fw-host0: SelfID received outside of bus reset sequence
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[6e56696469610000]
hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
hub 3-0:1.0: over-current change on port 2
hub 3-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
hub 3-0:1.0: Cannot enable port 2.  Maybe the USB cable is bad?
hub 3-0:1.0: over-current change on port 3
hub 3-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
hub 3-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
hub 3-0:1.0: over-current change on port 4
ohci_hcd 0000:00:02.1: wakeup
hub 3-0:1.0: over-current change on port 5
hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
hub 3-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
hub 3-0:1.0: over-current change on port 6
hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
hub 3-0:1.0: Cannot enable port 6.  Maybe the USB cable is bad?
usb 2-2: new low speed USB device using ohci_hcd and address 3
usbcore: registered new driver hiddev
input: USB HID v1.00 Mouse [Microsoft Microsoft Wheel Mouse Optical\uffff] on usb-000 0:00:02.1-2
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver

```

---

### Post by AgenT on 2005-04-09
While never using Ubuntu (I look forward to switching over from my current distro later), I would suggest that you do not use your HUB and first get all your hardware working. This will eliminate confusion. The first thing I would do is open up a terminal as root (or use sudo, please see [www.ubuntuguide.org]("http://www.ubuntuguide.org") if you need help with this step) and use the usb command:
 ```
lsusb
``` 
You would want to make sure that your hardware is activated. This means you want to not only plug in your printer but also turn it on. Then post the output. I am sure those that can help will appreciate it.

NOTE: Searching the best printer database website, [www.linuxprinting.org]("http://www.linuxprinting.org") shows that " USB is rumored to not work, but it is unclear why or what the problem was." This is for the HP DeskJet 895C. [[Reference]]("http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_895C")

Hope that helps!

---

### Post by PhilD on 2005-04-09
AgenT, lsusb reports:

Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

Which doesn't look too promising. I am not using any sort of external hub, all these ports came integrated on the motherboard.

I may have a parallel cable around here somewhere, maybe a good idea to dig it out...

---

### Post by AgenT on 2005-04-09
[QUOTE=PhilD]AgenT, lsusb reports:

Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

Which doesn't look too promising. I am not using any sort of external hub, all these ports came integrated on the motherboard.

I may have a parallel cable around here somewhere, maybe a good idea to dig it out...[/QUOTE]
 This does indeed look bad. Just in case, as a quick check I would open up term in root (or use sudo) and, before typing the lsusb command, would unplug the mouse and plug in the printer in its place (making sure the printer is on). I would wait about 30 seconds then type in lsusb. If it does not show up, that most likely means that [www.linuxprinting.org](www.linuxprinting.org) was right saying that "USB is rumored to not work". 

You can also get more information from lsusb by typing:
```
lsusb -v
```
Although I would imagine that this extra information will not help you (but just in case).

There is also the command (again, use root/sudo):
```
dmesg
```
This will show you realtime (well, sort of realtime since it only pulls the info once) system information. You will be able to see here an update when, for example, you unplug a USB device and, again, when you plug one in. dmesg is very helpful sometimes in troubleshooting.  The newest happenings will be listed on bottom. Again, not sure if this will help but, even if not, knowing about lsusb and dmesg is a good thing - there is also lspci which can take -vv to give PCI info)

---

### Post by PhilD on 2005-04-10
I got rid of the USB cable and used a good ol' fashioned parallel cable - printing now works. This is the first time I have ever got printing to work from Linux!

---

