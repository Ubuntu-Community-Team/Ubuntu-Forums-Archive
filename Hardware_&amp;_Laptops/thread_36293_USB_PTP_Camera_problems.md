---
title: "USB PTP Camera problems"
date: 2005-05-22
forum: Hardware &amp; Laptops
---

### Post by Steve White on 2005-05-22
I have a Sony DSC U20, which in PTP mode has given up its photos via USB to other Linux distro's.  So far Ubunto 5.04 is a no-go.  This is on an IBM T41p. 

It does not appear to be the permissions problem that I see in other posts: I can run software as root and I still have problems.

I have tried for front ends: gtkam, digikam, and in KDE, the camera gets mounted on the desktop, but when I try to open it with Konqueror, I get a similar message as  with all the other front ends.

If I run as an unpriviliged user, I get something like "Could not list folders in '/'", "PTP I/O error"; when I run as root, I get "Could not initialize camera." "PTP I/O error".

All indications are that USB sees the camera.  I see it listed in /proc/bus/usb/devices.  The auto-detect features of the camera front ends  find a similar Sony camera.

In /var/log/messages, I see something like
[INDENT]   usb 2-2: new full speed USB device using uhci_hcd and address 2
                usb.agent[9635]:      libgphoto2: loaded successfully
                usb 2-2: digikam timed out on ep2out
                usb 2-2: usbfs: USBDEVFS_BULK failed ep 0x2 le
[/INDENT]
Another curiosity: When I start any of the front ends looking for photos, the CD drive spins up! (and spins down when I cancel!)  Now, I don't think the CD is a USB device.  What gives?

So, where do I go from here?

---

### Post by David Haas on 2005-05-22
Steve--Since you are using Kubuntu, you might get better answers in the Kubuntu forum. In Gnome, I use the gThumb program to download images from my Nikon. Once the model is selected, one turns on the camera and then all the stored images appear as thumbnails in gThumb. 
Good luck,
David

---

### Post by Steve White on 2005-05-23
David, I think the symptoms indicate the problems lies at a level deeper than the desktop environment.  I'm thinking something like IRQ's.

But what the heck? Using Gthumb as root, when I click "Auto-detect", I get an error message.


[INDENT]   io-library ('Unspecified error'): Could not query kernel driver of device.[/INDENT]

Then it won't let me import.

And...the CD spins up, like before!  What is that?

---

### Post by David Haas on 2005-05-23
Steve---I see your point about where the problem seems to lie. I hope that someone in the Forum will be able to diagnose and remedy the glitch.
David

---

### Post by Steve White on 2005-05-26
Maybe the following is pertinent:  in my dmesg file, it looks like hotplug is running into problems:
[INDENT]cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: acpi_pciehprm:\_SB_.PCI0.PCI1 _HPP fail=0x5
pciehp: acpi_pciehprm:\_SB_.PCI0.PCI1 OSHP fails=0x5
pciehp: acpi_pciehprm:   Slot sun(1) at s:b:d:f=0x00:02:00:00
pciehp: acpi_pciehprm:\_SB_.PCI0.PCI1 _HPP fail=0x5
pciehp: acpi_pciehprm:\_SB_.PCI0.PCI1 OSHP fails=0x5
pciehp: acpi_pciehprm:   Slot sun(2) at s:b:d:f=0x00:02:00:01
pciehp: Fails to gain control of native hot-plug
shpchp: acpi_shpchprm:\_SB_.PCI0.PCI1 _HPP fail=0x5
shpchp: acpi_pciehprm:\_SB_.PCI0.PCI1 OSHP fails=0x5
shpchp: acpi_shpchprm:   Slot sun(1) at s:b:d:f=0x00:02:00:00
shpchp: acpi_shpchprm:\_SB_.PCI0.PCI1 _HPP fail=0x5
shpchp: acpi_pciehprm:\_SB_.PCI0.PCI1 OSHP fails=0x5
shpchp: acpi_shpchprm:   Slot sun(2) at s:b:d:f=0x00:02:00:01
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: shpc_init : shpc_cap_offset == 0
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v2.2
ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
ACPI: PCI interrupt 0000:00:1d.0[A] -> GSI 11 (level, low) -> IRQ 11
uhci_hcd 0000:00:1d.0: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
PCI: Setting latency timer of device 0000:00:1d.0 to 64
uhci_hcd 0000:00:1d.0: irq 11, io base 0x1800
uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
ACPI: PCI interrupt 0000:00:1d.1[B] -> GSI 11 (level, low) -> IRQ 11[/INDENT]
later
[INDENT]hw_random: RNG not detected
Evaluate _OSC Set fails. Status = 0x0005
pciehp: add_host_bridge: status 5
pciehp: acpi_pciehprm:\_SB_.PCI0.PCI1 _HPP fail=0x5
pciehp: acpi_pciehprm:\_SB_.PCI0.PCI1 OSHP fails=0x5
pciehp: acpi_pciehprm:   Slot sun(1) at s:b:d:f=0x00:02:00:00
pciehp: acpi_pciehprm:\_SB_.PCI0.PCI1 _HPP fail=0x5
pciehp: acpi_pciehprm:\_SB_.PCI0.PCI1 OSHP fails=0x5
pciehp: acpi_pciehprm:   Slot sun(2) at s:b:d:f=0x00:02:00:01
pciehp: Fails to gain control of native hot-plug
ACPI: PCI interrupt 0000:00:1f.5[B] -> GSI 11 (level, low) -> IRQ 11[/INDENT]

---

### Post by Steve White on 2005-06-11
I no longer think the hotplug pciehp and shpchp errors have anything to do with it.
I read they are due to excessive reporting on the part of those modules in cases where they aren't needed. (Work-around: include them in /etc/hotplug/blacklist).

---

### Post by Steve White on 2005-06-11
I tried something at a lower level.

[INDENT]```
env LANG=C gphoto2 --debug --debug --port "usb:" -L
```
[/INDENT]
The debug output looks normul until it tries to list the files

```
0.088057 gphoto2-setting(2): Setting key 'port' to value 'usb:' (gphoto2)
0.088440 gphoto2-setting(2): Saving 20 setting(s) to file "/home/swhite/.gphoto/settings"
0.089040 foreach(2): Executing action 'List Files' for folder '/'.
0.089872 gphoto2-camera(2): Listing files in '/'...
0.090224 gphoto2-camera(2): Initializing camera...
0.090562 gphoto2-port-usb(1): Looking for USB device (vendor 0x54c, product 0x4e)... found.
0.090985 gphoto2-port-usb(1): Detected defaults: config 1, interface 0, altsetting 0, inep 81, outep 02, intep 83, class 06, subclass 01
0.091494 gphoto2-camera(2): Loading '/usr/lib/gphoto2/2.1.5/libgphoto2_ptp2.so'...
0.092157 gphoto2-port(2): Opening USB port...
0.092693 gphoto2-port(0): Could not query kernel driver of device.
0.093076 gphoto2-port(2): Setting timeout to 8000 millisecond(s)...
0.093592 ptp(2): PTP: Opening session
0.093899 gphoto2-port(2): Writing 16=0x10 byte(s) to port...
0.094255 gphoto2-port(3): Hexdump of 16 = 0x10 bytes follows:
0000  10 00 00 00 01 00 02 10-00 00 00 00 01 00 00 00  ................

gp_port_write: Connection timed out
8.096214 PTP2/library.c(2): PTP: gp_port_* function returned 0xffffffdd         -35
8.096641 ptp(2): PTP: Opening session
8.096941 gphoto2-port(2): Writing 16=0x10 byte(s) to port...
8.097328 gphoto2-port(3): Hexdump of 16 = 0x10 bytes follows:
0000  10 00 00 00 01 00 02 10-00 00 00 00 01 00 00 00  ................

```

---

### Post by Steve White on 2005-07-23
I should report that I now have the camera working in "Normal" USB storage device mode.  PTP mode still does not work at all, but that isn't a problem for me any more.

---

