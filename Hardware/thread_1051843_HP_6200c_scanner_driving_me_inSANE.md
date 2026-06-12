---
title: "HP 6200c scanner driving me inSANE"
date: 2009-01-27
forum: Hardware
---

### Post by electrogeist on 2009-01-27
I have a HP 6200c, not current model but pretty nice scanner actually and well supported, it was a good find a few years back at a garage sale.  Been a while since I used it.  Has USB, SCSI, and ADB interfaces.  I am hoping to use USB.  If I stick a SCSI card in this box there will probably be 15K u/320 drives to follow, and as accomodating of a HTPC case Silverstone made I am restraining myself... so USB is the goal. I normally don't have a problem with USB, regularly plugging in jump drives and cameras and sh!t.  But I am not having luck with the scanner.  

I didn't keep notes of my first trials... had some errors occurring like "device descriptor read/64" and "device not accepting address" - but just previous to that I had to manually mount my jump drive (it didn't automount) and I decided to reboot starting from scratch in case something went wierd with the USB.  Current problems are Segfaults, Error during device I/O, scanner sometimes disappears from scanimage -L report, sometimes sane-find-scanner shows it without friendly device name.

I can *sometimes* get a simple black & white scan to work, sometimes with xsane, sometimes with scanimage on the command line.

So before I go into some more detailed output, here are a few things I tried:
- different cable
- different usb bus
- rmmod ehci_hcd 
- /etc/sane.d/hp.conf - option dumb-read
(# Uncomment the following if you have "Error during device I/O" on SCSI)
(using as USB but it is technically a SCSI scanner and I do get that error)

System specs:
- Intel D955XBK Blackcreek motherboard
- last of the netburst P4 Extreme Edition dual core
  (engineering sample, I sure as hell didn't buy retail! rock solid for years)
- nvidia 8600GT PCI-e video
- Hauppauge PVR-150
- WD Raptor + Maxtor SATA HDs, Sony or Lite-On DVD
- loaded with Corsair RAM thanks to craigslist
- HP 6200c (c6270) scanner
- Ubuntu 8.04 up to date



after a fresh reboot & plug in scanner:

```
$ dmesg
[  359.507784] usb 2-1: new full speed USB device using uhci_hcd and address 2
[  369.680364] usb 2-1: configuration #1 chosen from 1 choice

$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
Bus 003 Device 003: ID 0dc6:2011 Precision Squared Technology Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 03f0:0201 Hewlett-Packard ScanJet 6200c
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 001 Device 001: ID 0000:0000  

$ sane-find-scanner
found USB scanner (vendor=0x15c2, product=0xffdc) at libusb:003:004
found USB scanner (vendor=0x03f0 [Hewlett-Packard], product=0x0201 [HP ScanJet 6200C]) at libusb:002:002

$ scanimage -L
device `v4l:/dev/video0' is a Noname Hauppauge WinTV PVR-150 virtual device
device `hp:libusb:002:002' is a Hewlett-Packard ScanJet 62x0C flatbed scanner

$ scanimage -d hp:libusb:002:002  --format pnm > outfile.pnm
(sucessful!!)

$ scanimage -d hp:libusb:002:002  --format tiff > outfile.tiff
scanimage: sane_start: Error during device I/O
(WTF!)

$ scanimage -L
device `v4l:/dev/video0' is a Noname Hauppauge WinTV PVR-150 virtual device
device `hp:libusb:002:002' is a Hewlett-Packard ScanJet 62x0C flatbed scanner
(still sees the scanner!)

$ scanimage -d hp:libusb:002:002  --format tiff > outfile.tiff
scanimage: sane_start: Error during device I/O

$ scanimage -d hp:libusb:002:002  --format pnm > outfile.pnm
scanimage: sane_start: Error during device I/O

(nothing new in dmesg as of this point)


```


I had found removing the ehci_hcd module had helped some people with my previous errors so I tried it
```

$ sudo rmmod ehci_hcd 

$ dmesg
[ 1045.605371] ehci_hcd 0000:00:1d.7: remove, state 4
[ 1045.605388] usb usb5: USB disconnect, address 1
[ 1045.609788] ehci_hcd 0000:00:1d.7: USB bus 5 deregistered
[ 1045.610746] ACPI: PCI interrupt for device 0000:00:1d.7 disabled

$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
Bus 003 Device 003: ID 0dc6:2011 Precision Squared Technology Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 03f0:0201 Hewlett-Packard ScanJet 6200c
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 001 Device 001: ID 0000:0000  

$ sane-find-scanner 
found USB scanner (vendor=0x15c2, product=0xffdc) at libusb:003:004
found USB scanner (vendor=0x03f0 [Hewlett-Packard], product=0x0201 [HP ScanJet 6200C]) at libusb:002:002

~$ scanimage -L
device `v4l:/dev/video0' is a Noname Hauppauge WinTV PVR-150 virtual device

(missing HP! try again...)

$ scanimage -L
device `v4l:/dev/video0' is a Noname Hauppauge WinTV PVR-150 virtual device
device `hp:libusb:002:002' is a Hewlett-Packard ScanJet 62x0C flatbed scanner
(ok there it is!)

$ scanimage -d hp:libusb:002:002  --format pnm > outfile.pnm
(sucessful!!)

$ scanimage -d hp:libusb:002:002  --format tiff > outfile.tiff
Segmentation fault

$ dmesg
[ 1273.340436] scanimage[6639]: segfault at 10 rip 7fb7f0d1afa4 rsp 7ffff98b4900 error 4

$ scanimage -L
device `v4l:/dev/video0' is a Noname Hauppauge WinTV PVR-150 virtual device
device `hp:libusb:002:002' is a Hewlett-Packard ScanJet 62x0C flatbed scanner

$ xsane hp:libusb:002:002
dialog: Failed to open, Error during device I/O

$ scanimage -L
device `v4l:/dev/video0' is a Noname Hauppauge WinTV PVR-150 virtual device
device `hp:libusb:002:002' is a Hewlett-Packard ScanJet 62x0C flatbed scanner

Tried it again and it opens, but

$ xsane hp:libusb:002:002

$ scanimage -L
device `v4l:/dev/video0' is a Noname Hauppauge WinTV PVR-150 virtual device
(HP missing)

$ scanimage -L
scanimage: hp-option.c:3713: hp_optset_fix_geometry_options: Assertion `tl_x && tl_y && br_x && br_y' failed.
Aborted
(hmmm ?)

j@blackcreek:~$ scanimage -L
device `v4l:/dev/video0' is a Noname Hauppauge WinTV PVR-150 virtual device
(HP still missing)

$ dmesg
[ 1606.047611] usb 2-1: usbfs: interface 0 claimed by usbfs while 'scanimage' sets config #1
[ 1656.963024] usb 2-1: usbfs: interface 0 claimed by usbfs while 'scanimage' sets config #1
[ 1660.880459] usb 2-1: usbfs: interface 0 claimed by usbfs while 'scanimage' sets config #1

```



unplug and replug scanner
```

$ dmesg
[ 1806.382115] usb 2-1: USB disconnect, address 2
[ 1814.151781] usb 2-1: new full speed USB device using uhci_hcd and address 3
[ 1824.320370] usb 2-1: configuration #1 chosen from 1 choice

$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
Bus 003 Device 003: ID 0dc6:2011 Precision Squared Technology Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 03f0:0201 Hewlett-Packard ScanJet 6200c
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 001 Device 001: ID 0000:0000  

$ scanimage -L
device `v4l:/dev/video0' is a Noname Hauppauge WinTV PVR-150 virtual device
device `hp:libusb:002:003' is a Hewlett-Packard ScanJet 62x0C flatbed scanner

$ xsane hp:libusb:002:003
b&w lineart scan #1 works
b&w lineart scan #2 works again
grayscale scan #1 = Error during read: Error during device I/O
grayscale scan #2 = Segmentation fault

$ dmesg
[ 2307.454767] xsane[6801]: segfault at 0 rip 7fc8abd7a080 rsp 7fffb8632f78 error 4

$ rm -r ~/.sane

$ sane-find-scanner 
found USB scanner (vendor=0x15c2, product=0xffdc) at libusb:003:004
found USB scanner (vendor=0x03f0, product=0x0201) at libusb:002:003
(notice its not reporting brand name)

$ scanimage -L
device `v4l:/dev/video0' is a Noname Hauppauge WinTV PVR-150 virtual device
(HP missing, tried several times)

```

unplug and replug scanner again
```

$ dmesg
[ 2659.858902] usb 2-1: USB disconnect, address 3
[ 2667.336954] usb 2-1: new full speed USB device using uhci_hcd and address 4
[ 2677.505548] usb 2-1: configuration #1 chosen from 1 choice

$ sane-find-scanner 
found USB scanner (vendor=0x15c2, product=0xffdc) at libusb:003:004
found USB scanner (vendor=0x03f0 [Hewlett-Packard], product=0x0201 [HP ScanJet 6200C]) at libusb:002:004


$ scanimage -L
device `v4l:/dev/video0' is a Noname Hauppauge WinTV PVR-150 virtual device
device `hp:libusb:002:004' is a Hewlett-Packard ScanJet 62x0C flatbed scanner

$ xsane hp:libusb:002:004

b&w lineart scan = Error during read: Error during device I/O

$ scanimage -L
device `v4l:/dev/video0' is a Noname Hauppauge WinTV PVR-150 virtual device
(missing HP)

$ sane-find-scanner
found USB scanner (vendor=0x15c2, product=0xffdc) at libusb:003:004
found USB scanner (vendor=0x03f0, product=0x0201) at libusb:002:004
(notice its not reporting brand name)

$ dmesg
[ 2939.058192] usb 2-1: usbfs: interface 0 claimed by usbfs while 'scanimage' sets config #1
[ 2959.225262] usb 2-1: usbfs: USBDEVFS_CONTROL failed cmd sane-find-scann rqt 128 rq 6 len 2 ret -71
[ 2959.226251] usb 2-1: usbfs: USBDEVFS_CONTROL failed cmd sane-find-scann rqt 128 rq 6 len 2 ret -71

```


unplug and replug scanner
```

$ dmesg
[ 3445.968980] usb 2-1: USB disconnect, address 4
[ 3452.228650] usb 2-1: new full speed USB device using uhci_hcd and address 5
[ 3462.397264] usb 2-1: configuration #1 chosen from 1 choice

$ sane-find-scanner
found USB scanner (vendor=0x15c2, product=0xffdc) at libusb:003:004
found USB scanner (vendor=0x03f0 [Hewlett-Packard], product=0x0201 [HP ScanJet 6200C]) at libusb:002:005

$ scanimage -L
device `v4l:/dev/video0' is a Noname Hauppauge WinTV PVR-150 virtual device
device `hp:libusb:002:005' is a Hewlett-Packard ScanJet 62x0C flatbed scanner

$ scanimage -d hp:libusb:002:005  --format tiff > outfile.tiff
Segmentation fault

$ dmesg
[ 3639.363431] scanimage[7057]: segfault at 10 rip 7f709565dfa4 rsp 7fff9e1f5220 error 4

```

---

