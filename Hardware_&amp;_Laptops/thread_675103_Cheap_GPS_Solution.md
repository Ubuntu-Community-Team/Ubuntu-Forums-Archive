---
title: "Cheap GPS Solution"
date: 2008-01-22
forum: Hardware &amp; Laptops
---

### Post by partypants69 on 2008-01-22
I just installed Ubuntu 7.10 on an HP530 and I would love to get a GPS receiver working on it. After looking for them online, I found this generic brand one for about $28 including shipping. I am brand new to linux and have been having a very tough time getting it to work. The driver that comes with it is for Vista or XP only. I have tried using NDISWrapper to get it to work, with no luck. I am hoping the linux community can come through for me on this one. If we had a working driver for this device, it would mean a very inexpensive GPS solution for everyone. I'm not sure how many people out there are using GPS on linux, or how much their receivers cost them, but I imagine this is one of the cheapest out there. By the way, I did test the receiver on windows and it does work. The link for the device is: [http://www.geeks.com/details.asp?invtid=MS-GD-03&cat=GPS](http://www.geeks.com/details.asp?invtid=MS-GD-03&cat=GPS)

If anyone out there feels like writing a driver, or would like the windows drivers for the device I would be more than happy to send them. Also if anyone has a solution already that I am unaware of please let me know.

-Linux n00b

---

### Post by kevinatkins on 2008-01-22
Hi,

I haven't got any experience of GPS on linux but it sounds like a fantastic idea - I'm going to start looking into this myself..

Anyway, a quick dig on Google and I turned this up -

[http://tuxmobil.org/navigation_gps.html](http://tuxmobil.org/navigation_gps.html)

It might be a starting point - I think you'll be better off (initially) using Google, to cast your net beyond Ubuntu specifically....

---

### Post by partypants69 on 2008-01-24
That may be true, I did search google before posting here, but it may be worth some more time.

---

### Post by tgalati4 on 2008-01-24
After you plug it in, what is the output of:

dmesg | tail -25

---

### Post by partypants69 on 2008-01-24
This is the output after plugging it in.

```
[  182.959052] Failure registering capabilities with primary security module.
[  183.781356] Bluetooth: Core ver 2.11
[  183.781538] NET: Registered protocol family 31
[  183.781543] Bluetooth: HCI device and connection manager initialized
[  183.781548] Bluetooth: HCI socket layer initialized
[  183.877424] Bluetooth: L2CAP ver 2.8
[  183.877431] Bluetooth: L2CAP socket layer initialized
[  184.094412] Bluetooth: RFCOMM socket layer initialized
[  184.094578] Bluetooth: RFCOMM TTY layer initialized
[  184.094584] Bluetooth: RFCOMM ver 1.8
[  189.164614] NET: Registered protocol family 17
[  191.184837] [drm] Initialized drm 1.1.0 20060810
[  191.244949] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 20
[  191.249190] [drm] Initialized radeon 1.27.0 20060524 on minor 0
[  193.688216] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[  193.688246] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[  193.688338] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[  193.967212] [drm] Setting GART location based on new memory map
[  193.967225] [drm] Loading R300 Microcode
[  193.967283] [drm] writeback test succeeded in 1 usecs
[  195.680537] NET: Registered protocol family 10
[  195.680893] lo: Disabled Privacy Extensions
[  206.114201] eth0: no IPv6 routers present
[  316.851335] usb 5-2: new high speed USB device using ehci_hcd and address 2
[  316.983665] usb 5-2: configuration #1 chosen from 1 choice

```

---

### Post by tgalati4 on 2008-01-25
Post the output of:

lsusb

---

### Post by partypants69 on 2008-01-25
lsusb returns:

```
Bus 005 Device 003: ID 0471:082d Philips 
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  

```

---

### Post by tgalati4 on 2008-01-25
I've had good luck with these:

[http://www.usglobalsat.com/p-62-bu-353.aspx](http://www.usglobalsat.com/p-62-bu-353.aspx) (they were ~$80 last year), the older versions are about $40 using SirFStarII which don't work well indoors or in cars)

Your USB gps device is not showing up.  The globalsat devices use a USB-to-serial driver call PL2303 which converts the USB data stream to serial data for the gps device.  Since  your device is not showing up as a recognized device, you will have to force load a driver.

Try:

sudo modprobe pl2303

Then try installing gpsdrive and set up the device in preferences to use serial protocol.

There's a reason it was so cheap.  There's probably only a Windows driver.  I assume that you have tested it under Windows.  If you can get it to work with another driver, then that's worth sharing.  You will have to investigate what chipset the device is using.  Is it a SirFStar III?  That's the best chipset on the market currently for USB devices.  

Try contacting the manufacturer for a Linux driver.

---

