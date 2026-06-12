---
title: "Can't get any USB drive to work??"
date: 2006-07-24
forum: Hardware &amp; Laptops
---

### Post by madscientist on 2006-07-24
I've been trying to get USB drives to work and it just won't!  I was using Debian and I figured maybe I just didn't have something set up right.  I wanted to switch to Ubuntu anyway (I was already using it on other systems) so I installed 6.06, but I still can't get it to work for me.  I plug in the drive and nothing happens.  I use "lsusb" and it doesn't even see the drive:

$ lsusb -t
Bus#  4
`-Dev#   1 Vendor 0x0000 Product 0x0000
Bus#  3
`-Dev#   1 Vendor 0x0000 Product 0x0000
Bus#  2
`-Dev#   1 Vendor 0x0000 Product 0x0000
Bus#  1
`-Dev#   1 Vendor 0x0000 Product 0x0000

I know it's plugged in because the drive gets power and the LED lights up for a few seconds, then the light goes out until I unplug/replug it.  I tried it on a Windows XP box at a relatives house and it worked fine, no special drivers needed to be installed.

The drive is a Dane-Elec USB 2.0 9-in-4 reader/writer: [this one]("http://www.dane-elec.fr/home/liblocal/DOCS/Doc%20Mkg%20(UK)/COMBO9in4-UK.pdf").

Anyone have any thoughts about what I can do next and where to go from here?  I'm using a completely up-to-date Ubuntu 6.06, but I built my own kernel (using make-kpkg) from Linux 2.6.16.19, starting with the config for the default Ubuntu kernel.  My system is an ad-hoc black box system.  lspci says this about my USB controllers:

0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)

Hm.  Does that mean that only one of my four USB ports is actually USB 2.0?  How do I figure out which one it is?

I also see some errors in my dmesg output:

usb usb3: configuration #1 chosen from 1 choice
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 2 ports detected
ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
ACPI: PCI Interrupt 0000:00:10.3[D] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ
 10
ehci_hcd 0000:00:10.3: EHCI Host Controller
ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
ehci_hcd 0000:00:10.3: irq 10, io mem 0xdfffff00
ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
usb usb4: configuration #1 chosen from 1 choice
hub 4-0:1.0: USB hub found
hub 4-0:1.0: 6 ports detected
EXT3-fs: INFO: recovery required on readonly filesystem.
EXT3-fs: write access will be enabled during recovery.
usb 3-2: new low speed USB device using uhci_hcd and address 2
usb 3-2: device descriptor read/64, error -71
usb 3-2: device descriptor read/64, error -71
usb 3-2: new low speed USB device using uhci_hcd and address 3
usb 3-2: device descriptor read/64, error -71
usb 3-2: device descriptor read/64, error -71
usb 3-2: new low speed USB device using uhci_hcd and address 4
usb 3-2: device not accepting address 4, error -71
usb 3-2: new low speed USB device using uhci_hcd and address 5
usb 3-2: device not accepting address 5, error -71

---

### Post by madscientist on 2006-07-25
Aha!  It *was* a USB 1.1 vs. 2.0 problem.  I found another post somewhere else saying that plugging a 2.0 device into a 1.1 port can give odd errors like the -71 I was seeing, so I tried all the USB ports.  Unfortunately both the front panel ports on my system are 1.1, but I found one of the rear ports that works fine.  I have a USB extender cable so I can just run it up front anyway.

Cool!

---

