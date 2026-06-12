---
title: "[SOLVED] Samsung M2885FW MFP printer"
date: 2015-02-28
forum: Hardware
---

### Post by phoenix1963 on 2015-02-28
Hi all, I've just bought a Samsung M2285FW mono printer/scanner on the basis that Samsung support linux. I used the samsung install.sh script, it seems connected over the usb, but also over the wifi network. CUPS sees it, but even if I try and get CUPS to print a test page, nothing happens.

here is the output in /var/log/syslog when I connect it:
```

Feb 28 21:00:22 lbox2 udev-configure-printer: URI of detected printer: usb://Samsung/M288x%20Series?serial=071UBJDF80004PF&interface=1, normalized: samsung m288x series serial 071ubjdf80004pf interface 1
Feb 28 21:00:22 lbox2 udev-configure-printer: URI of print queue: usb://Samsung/M288x%20Series?serial=071UBJDF80004PF&interface=1, normalized: samsung m288x series serial 071ubjdf80004pf interface 1
Feb 28 21:00:22 lbox2 udev-configure-printer: URI of detected printer: usb://Samsung/M288x%20Series?serial=071UBJDF80004PF&interface=1, normalized: samsung m288x series serial 071ubjdf80004pf interface 1
Feb 28 21:00:22 lbox2 udev-configure-printer: Queue ipp://localhost:631/printers/M288x-Series has matching device URI
Feb 28 21:00:22 lbox2 udev-configure-printer: Disabled printer ipp://localhost:631/printers/M288x-Series as the corresponding device was unplugged or turned off
Feb 28 21:00:47 lbox2 kernel: [13375.544035] usb 2-2: new high-speed USB device number 4 using ehci_hcd
Feb 28 21:00:47 lbox2 kernel: [13375.684881] usblp0: USB Bidirectional printer dev 4 if 1 alt 0 proto 2 vid 0x04E8 pid 0x346A
Feb 28 21:00:47 lbox2 udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2:1.1
Feb 28 21:00:47 lbox2 udev-configure-printer: device devpath is /devices/pci0000:00/0000:00:1d.7/usb2/2-2
Feb 28 21:00:47 lbox2 udev-configure-printer: Device vendor/product is 04E8:346A
Feb 28 21:00:47 lbox2 udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2:1.1/usb/lp0
Feb 28 21:00:47 lbox2 udev-configure-printer: failed to claim interface
Feb 28 21:00:47 lbox2 udev-configure-printer: device devpath is /devices/pci0000:00/0000:00:1d.7/usb2/2-2
Feb 28 21:00:47 lbox2 udev-configure-printer: MFG:Samsung MDL:M288x Series SERN:- serial:071UBJDF80004PF
Feb 28 21:00:48 lbox2 kernel: [13376.909544] usblp0: removed
Feb 28 21:00:48 lbox2 kernel: [13376.921436] usblp0: USB Bidirectional printer dev 4 if 1 alt 0 proto 2 vid 0x04E8 pid 0x346A
Feb 28 21:00:48 lbox2 udev-configure-printer: add /devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2:1.1/usb/lp0
Feb 28 21:00:48 lbox2 hp[13403]: io/hpmud/pp.c 627: unable to read device-id ret=-1
Feb 28 21:00:48 lbox2 python: io/hpmud/pp.c 627: unable to read device-id ret=-1
Feb 28 21:00:49 lbox2 udev-configure-printer: URI contains USB serial number
Feb 28 21:00:49 lbox2 udev-configure-printer: URI match: usb://Samsung/M288x%20Series?serial=071UBJDF80004PF&interface=1
Feb 28 21:00:49 lbox2 udev-configure-printer: device devpath is /devices/pci0000:00/0000:00:1d.7/usb2/2-2
Feb 28 21:00:49 lbox2 udev-configure-printer: Device already handled
Feb 28 21:00:49 lbox2 udev-configure-printer: Consider also queues with "/usb/lp0" or "/usblp0" in their URIs as matching
Feb 28 21:00:49 lbox2 udev-configure-printer: URI of print queue: dnssd://HP%20LaserJet%20CP1025nw._pdl-datastream._tcp.local/, normalized: dnssd hp laserjet cp1025nw pdl datastream tcp local
Feb 28 21:00:49 lbox2 udev-configure-printer: URI of detected printer: usb://Samsung/M288x%20Series?serial=071UBJDF80004PF&interface=1, normalized: samsung m288x series serial 071ubjdf80004pf interface 1
Feb 28 21:00:49 lbox2 udev-configure-printer: URI of print queue: usb://Samsung/M288x%20Series?serial=071UBJDF80004PF&interface=1, normalized: samsung m288x series serial 071ubjdf80004pf interface 1
Feb 28 21:00:49 lbox2 udev-configure-printer: URI of detected printer: usb://Samsung/M288x%20Series?serial=071UBJDF80004PF&interface=1, normalized: samsung m288x series serial 071ubjdf80004pf interface 1
Feb 28 21:00:49 lbox2 udev-configure-printer: Queue ipp://localhost:631/printers/M288x-Series has matching device URI
Feb 28 21:00:49 lbox2 udev-configure-printer: IPP-Resume-Printer request failed

```

lusb gives:
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 04e8:346a Samsung Electronics Co., Ltd 
Bus 006 Device 002: ID 0461:4de3 Primax Electronics, Ltd 

```

and ls -l /dev/usb/lp* /dev/bus/usb/*/* shows:
```

crw-rw-r--  1 root root 189,   0 Feb 28 17:18 /dev/bus/usb/001/001
crw-rw-r--  1 root root 189, 128 Feb 28 17:18 /dev/bus/usb/002/001
crw-rw----+ 1 root root 189, 131 Feb 28 21:00 /dev/bus/usb/002/004
crw-rw-r--  1 root root 189, 256 Feb 28 17:18 /dev/bus/usb/003/001
crw-rw-r--  1 root root 189, 384 Feb 28 17:18 /dev/bus/usb/004/001
crw-rw-r--  1 root root 189, 512 Feb 28 17:18 /dev/bus/usb/005/001
crw-rw-r--  1 root root 189, 640 Feb 28 17:18 /dev/bus/usb/006/001
crw-rw-r--  1 root root 189, 641 Feb 28 17:18 /dev/bus/usb/006/002
crw-rw-r--  1 root root 189, 768 Feb 28 17:18 /dev/bus/usb/007/001
crw-rw-r--+ 1 root lp   180,   0 Feb 28 21:00 /dev/usb/lp0

```

and sudo usb_printerid /dev/usb/lp0 gives:
```

GET_DEVICE_ID string:
MFG:Samsung;CMD:SPL,PCL6,URF,FAX,FWV,PIC,SPDS,EXT;MDL:M288x Series;CLS:PRINTER;CID:SA_PCL6_BW;MODE:FAX3,SCN,SPL3,R000105;STATUS:BUSY;

```

while lpinfo -v shows:
```

network ipp14
network socket
network beh
network https
network http
network ipps
network lpd
network ipp
network smb
direct parallel:/dev/lp0
direct usb://Samsung/M288x%20Series?serial=071UBJDF80004PF&interface=1
direct hp
direct hpfax
network dnssd://Samsung%20M288x%20Series%20(SEC30CDA73209DA)._ipp._tcp.local/
network dnssd://Samsung%20M288x%20Series%20(SEC30CDA73209DA)._printer._tcp.local/
network dnssd://Samsung%20M288x%20Series%20(SEC30CDA73209DA)._pdl-datastream._tcp.local/
network ipp://172.16.1.113
network socket://172.16.1.113

```

I can log in to the printer's web server at the local ip, but even there, if I try to print a test page, nothing happens.

Has anyone got any clues?

phoenix1963

---

### Post by phoenix1963 on 2015-02-28
Sorry everyone... I needed to press the "ready to scan" button on the printer control panel. That made it "ready to print".

really logical, eh?

A few glasses of wine seemed to help with the solution ;)

phoenix1963

---

