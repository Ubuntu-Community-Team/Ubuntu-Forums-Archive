---
title: "hp officejet 4500 not detected by lsusb but detected by sane-find-scanner in Lucid"
date: 2011-11-09
forum: Hardware
---

### Post by Vpc on 2011-11-09
I upgraded to ubuntu 10.04 from 8.04 recently. When I try to use Simple Scan it says "No scanners detected". sane-find-scanner detects my printer/scanner but lsusb does not. Also I am able to print from my printer so it's just a problem with the scanner and lsusb. 

```

administrator@snoopy:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

administrator@snoopy:~$ sudo sane-find-scanner
[sudo] password for administrator: 

# sane-find-scanner will now attempt to detect your scanner. If the
# result is different from what you expected, first make sure your
# scanner is powered up and properly connected to your computer.

# No SCSI scanners found. If you expected something different, make sure that
# you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x03f0 [HP], product=0x4712 [Officejet 4500 G510a-f]) at libusb:001:005
# Your USB scanner was (probably) detected. It may or may not be supported by
# SANE. Try scanimage -L and read the backend's manpage.

# Not checking for parallel port scanners.

# Most Scanners connected to the parallel port or other proprietary ports
# can't be detected by this program.

administrator@snoopy:~$ dmesg | grep usb
[    0.124495] usbcore: registered new interface driver usbfs
[    0.124519] usbcore: registered new interface driver hub
[    0.124574] usbcore: registered new device driver usb
[    0.312547] usb usb1: configuration #1 chosen from 1 choice
[    0.313151] usb usb2: configuration #1 chosen from 1 choice
[    0.313627] usb usb3: configuration #1 chosen from 1 choice
[    0.314062] usb usb4: configuration #1 chosen from 1 choice
[    0.314486] usb usb5: configuration #1 chosen from 1 choice
[    0.900795] usb 3-2: new low speed USB device using uhci_hcd and address 2
[    1.122525] usb 3-2: configuration #1 chosen from 1 choice
[    1.429716] usbcore: registered new interface driver hiddev
[    1.431864] usbcore: registered new interface driver usbhid
[    1.433611] usbhid: v2.6:USB HID core driver
[    1.560705] input: Microsoft Natural® Ergonomic Keyboard 4000 as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input3
[    1.560882] microsoft 0003:045E:00DB.0001: input,hidraw0: USB HID v1.11 Keyboard [Microsoft Natural® Ergonomic Keyboard 4000] on usb-0000:00:1d.1-2/input0
[    1.584491] input: Microsoft Natural® Ergonomic Keyboard 4000 as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.1/input/input4
[    1.584673] microsoft 0003:045E:00DB.0002: input,hidraw1: USB HID v1.11 Device [Microsoft Natural® Ergonomic Keyboard 4000] on usb-0000:00:1d.1-2/input1
[163980.380089] usb 1-3: new high speed USB device using ehci_hcd and address 3
[163980.514030] usb 1-3: configuration #1 chosen from 1 choice
[163982.225839] usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x03F0 pid 0x4712
[163982.225904] usbcore: registered new interface driver usblp
[163984.395465] usb 1-3: usbfs: interface 1 claimed by usblp while 'usb' sets config #1


```

In var/log/syslog:

Nov  9 11:14:18 snoopy kernel: [40994.348199] usb 1-3: new high speed USB device using ehci_hcd and address 3
Nov  9 11:14:18 snoopy kernel: [40994.484270] usb 1-3: configuration #1 chosen from 1 choice
Nov  9 11:14:20 snoopy udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3:1.1
Nov  9 11:14:20 snoopy kernel: [40996.551347] usblp0: USB Bidirectional printer dev 3 if 1 alt 0 proto 2 vid 0x03F0 pid 0x4712
Nov  9 11:14:20 snoopy kernel: [40996.551407] usbcore: registered new interface driver usblp
Nov  9 11:14:20 snoopy udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb1/1-3
Nov  9 11:14:20 snoopy udev-configure-printer: Device vendor/product is 03F0:4712
Nov  9 11:14:20 snoopy udev-configure-printer: failed to claim interface
Nov  9 11:14:20 snoopy udev-configure-printer: invalid or missing IEEE 1284 Device ID
Nov  9 11:14:21 snoopy udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3:1.1/usb/lp0
Nov  9 11:14:21 snoopy udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb1/1-3
Nov  9 11:14:21 snoopy udev-configure-printer: MFG:HP MDL:Officejet 4500 G510a-f SERN:CN049F20C905H2 serial:CN049F20C905H2
Nov  9 11:14:23 snoopy kernel: [40999.240548] usb 1-3: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
Nov  9 11:14:23 snoopy hp[4537]: io/hpmud/pp.c 627: unable to read device-id ret=-1
Nov  9 11:14:25 snoopy udev-configure-printer: SERN fields match
Nov  9 11:14:25 snoopy udev-configure-printer: URI match: usb://HP/Officejet%204500%20G510a-f?serial=CN049F20C905H2
Nov  9 11:14:25 snoopy udev-configure-printer: SERN fields match
Nov  9 11:14:25 snoopy udev-configure-printer: URI match: hp:/usb/Officejet_4500_G510a-f?serial=CN049F20C905H2
Nov  9 11:14:25 snoopy udev-configure-printer: Consider also queues with "/usb/lp0" or "/usblp0" in their URIs as matching
Nov  9 11:14:25 snoopy udev-configure-printer: URI of print queue: hp:/usb/Officejet_4500_G510a-f?serial=CN049F20C905H2, normalized: officejet 4500 g510a f serial cn049f20c905h2
Nov  9 11:14:25 snoopy udev-configure-printer: URI of detected printer: usb://HP/Officejet%204500%20G510a-f?serial=CN049F20C905H2, normalized: officejet 4500 g510a f serial cn049f20c905h2
Nov  9 11:14:25 snoopy udev-configure-printer: Queue ipp://localhost:631/printers/Officejet_4500_G510a-f has matching device URI
Nov  9 11:14:25 snoopy udev-configure-printer: Re-enabled printer ipp://localhost:631/printers/Officejet_4500_G510a-f
Nov  9 11:14:25 snoopy udev-configure-printer: URI of detected printer: hp:/usb/Officejet_4500_G510a-f?serial=CN049F20C905H2, normalized: officejet 4500 g510a f serial cn049f20c905h2
Nov  9 11:14:25 snoopy udev-configure-printer: Queue ipp://localhost:631/printers/Officejet_4500_G510a-f has matching device URI
Nov  9 11:14:26 snoopy udev-configure-printer: Re-enabled printer ipp://localhost:631/printers/Officejet_4500_G510a-f
Nov  9 11:14:26 snoopy udev-configure-printer: URI of print queue: hp:/usb/Officejet_4500_G510a-f?serial=CN049F20C905H2, normalized: officejet 4500 g510a f serial cn049f20c905h2
Nov  9 11:14:26 snoopy udev-configure-printer: URI of detected printer: usb://HP/Officejet%204500%20G510a-f?serial=CN049F20C905H2, normalized: officejet 4500 g510a f serial cn049f20c905h2
Nov  9 11:14:26 snoopy udev-configure-printer: Queue ipp://localhost:631/printers/Officejet_4500_G510a-f_2 has matching device URI
Nov  9 11:14:26 snoopy udev-configure-printer: Re-enabled printer ipp://localhost:631/printers/Officejet_4500_G510a-f_2
Nov  9 11:14:26 snoopy udev-configure-printer: URI of detected printer: hp:/usb/Officejet_4500_G510a-f?serial=CN049F20C905H2, normalized: officejet 4500 g510a f serial cn049f20c905h2
Nov  9 11:14:26 snoopy udev-configure-printer: Queue ipp://localhost:631/printers/Officejet_4500_G510a-f_2 has matching device URI
Nov  9 11:14:26 snoopy udev-configure-printer: Re-enabled printer ipp://localhost:631/printers/Officejet_4500_G510a-f_2
Nov  9 11:14:26 snoopy udev-configure-printer: URI of print queue: hpfax:/usb/Officejet_4500_G510a-f?serial=CN049F20C905H2, normalized: hpfax usb officejet 4500 g510a f serial cn049f20c905h2
Nov  9 11:14:26 snoopy udev-configure-printer: URI of detected printer: usb://HP/Officejet%204500%20G510a-f?serial=CN049F20C905H2, normalized: officejet 4500 g510a f serial cn049f20c905h2
Nov  9 11:14:26 snoopy udev-configure-printer: URI of detected printer: hp:/usb/Officejet_4500_G510a-f?serial=CN049F20C905H2, normalized: officejet 4500 g510a f serial cn049f20c905h2
Nov  9 11:14:26 snoopy udev-configure-printer: URI of print queue: hpfax:/usb/Officejet_4500_G510a-f?serial=CN049F20C905H2, normalized: hpfax usb officejet 4500 g510a f serial cn049f20c905h2
Nov  9 11:14:26 snoopy udev-configure-printer: URI of detected printer: usb://HP/Officejet%204500%20G510a-f?serial=CN049F20C905H2, normalized: officejet 4500 g510a f serial cn049f20c905h2
Nov  9 11:14:26 snoopy udev-configure-printer: URI of detected printer: hp:/usb/Officejet_4500_G510a-f?serial=CN049F20C905H2, normalized: officejet 4500 g510a f serial cn049f20c905h2
Nov  9 11:14:26 snoopy udev-configure-printer: URI of print queue: hpfax:/usb/Officejet_4500_G510a-f?serial=CN049F20C905H2, normalized: hpfax usb officejet 4500 g510a f serial cn049f20c905h2
Nov  9 11:14:26 snoopy udev-configure-printer: URI of detected printer: usb://HP/Officejet%204500%20G510a-f?serial=CN049F20C905H2, normalized: officejet 4500 g510a f serial cn049f20c905h2
Nov  9 11:14:26 snoopy udev-configure-printer: URI of detected printer: hp:/usb/Officejet_4500_G510a-f?serial=CN049F20C905H2, normalized: officejet 4500 g510a f serial cn049f20c905h2
Nov  9 11:14:26 snoopy udev-configure-printer: URI of print queue: cups-pdf:/, normalized: cups pdf
Nov  9 11:14:26 snoopy udev-configure-printer: URI of detected printer: usb://HP/Officejet%204500%20G510a-f?serial=CN049F20C905H2, normalized: officejet 4500 g510a f serial cn049f20c905h2
Nov  9 11:14:26 snoopy udev-configure-printer: URI of detected printer: hp:/usb/Officejet_4500_G510a-f?serial=CN049F20C905H2, normalized: officejet 4500 g510a f serial cn049f20c905h2

Also I am unable to access my modem configuration at [http://192.168.1.254/](http://192.168.1.254/) as I am continuously prompted for my user name and password. I was able to access the configuration page before the upgrade. My ISP confirmed I have the correct info. So could there be a problem with the software used to communicate with devices? 

I know dbus was part of the upgrade & I think I installed a new version from the source (and I think some other packages) when I didn't have an internet connection and was trying to complete the upgrade. I also followed tips to fix a common problem with the password ring. Should I re-install the dbus package or some other packages?

My computer is several years old, don't have the exact age. I have installed all the latest software updates according to Update Manager. My processor: model name : Intel(R) Celeron(R) CPU 2.40GHz stepping : 4 cpu MHz : 2394.331 cache size : 256 KB

---

### Post by Vpc on 2011-11-11
Simple Scan and `lsusb` detects the scanner after doing the following:

1. Install hplip and hplip-cups using System>Administration>Synaptic Package Manager. In my case, before clicking 'Apply' in the package manager, I had to go to Settings>Repositories and uncheck 'Cdrom with Ubuntu 10.04' in the 'Installable from CD-ROM/DVD' box at the bottom in order for the necessary packages to be downloaded.
2. Run `hp-check -r`
3. In my case, the output said that the user 'root' needed to be in the 'lp' and 'lp-admin' groups so I used `usermod -G group-name user-name` to add 'root' to those groups.

---

