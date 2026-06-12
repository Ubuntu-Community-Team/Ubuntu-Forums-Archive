---
title: "USB-connected Brother MFC-8220 printer not found after moving to 16.04"
date: 2017-08-26
forum: Hardware
---

### Post by ian.macky on 2017-08-26
[TABLE="class: cke_editor"]
[TR]
[TD="class: cke_contents"]My Brother MFC-8220 printer used to work fine when I was running 12.04, but after installing 16.04 (on a new HD) it's kaput.  I've spent many hours over the last two days reading forum posts on many sites, and tried many things, but no joy.  Frustrated!

% lsusb|grep Bro
Bus 001 Device 003: ID 04f9:0150 Brother Industries, Ltd MFC-8220 Port(FaxModem)

It all seems to go wrong here (same errors on boot or after unplugging and plugging the USB cable):

```
Aug 24 15:41:28 spunky kernel: usb 1-5: new high-speed USB device number 3 using ehci-pci
Aug 24 15:41:28 spunky kernel: usb 1-5: New USB device found, idVendor=04f9, idProduct=0150
Aug 24 15:41:28 spunky kernel: usb 1-5: New USB device strings: Mfr=0, Product=0, SerialNumber=3
Aug 24 15:41:28 spunky kernel: usb 1-5: SerialNumber: 000J4J171991
Aug 24 15:41:28 spunky mtp-probe[1085]: checking bus 1, device 3: "/sys/devices/pci0000:00/0000:00:13.2/usb1/1-5"
Aug 24 15:41:29 spunky mtp-probe[1085]: bus: 1, device: 3 was not an MTP device
Aug 24 15:41:29 spunky systemd[1]: Reached target Printer.
Aug 24 15:41:29 spunky systemd[1]: Starting Automatic USB/Bluetooth printer setup (-devices-pci0000:00-0000:00:13.2-usb1-1\x2d5)...
Aug 24 15:41:29 spunky udev-configure-printer[1090]: add /devices/pci0000:00/0000:00:13.2/usb1/1-5
Aug 24 15:41:29 spunky udev-configure-printer[1090]: device devpath is /devices/pci0000:00/0000:00:13.2/usb1/1-5
Aug 24 15:41:29 spunky udev-configure-printer[1090]: Device vendor/product is 04F9:0150
Aug 24 15:41:35 spunky udev-configure-printer[1090]: Failed to fetch Device ID
Aug 24 15:41:35 spunky systemd[1]: [EMAIL="udev-configure-printer@-devices-pci0000:00-0000:00:13.2-usb1-1\x2d5.servic"]udev-configure-printer@-devices-pci0000:00-0000:00:13.2-usb1-1\x2d5.servic[/EMAIL]e: Control process exited, code=exited status=1
Aug 24 15:41:35 spunky systemd[1]: Failed to start Automatic USB/Bluetooth printer setup (-devices-pci0000:00-0000:00:13.2-usb1-1\x2d5).
Aug 24 15:41:35 spunky systemd[1]: [EMAIL="udev-configure-printer@-devices-pci0000:00-0000:00:13.2-usb1-1\x2d5.servic"]udev-configure-printer@-devices-pci0000:00-0000:00:13.2-usb1-1\x2d5.servic[/EMAIL]e: Unit entered failed state.
Aug 24 15:41:35 spunky systemd[1]: [EMAIL="udev-configure-printer@-devices-pci0000:00-0000:00:13.2-usb1-1\x2d5.servic"]udev-configure-printer@-devices-pci0000:00-0000:00:13.2-usb1-1\x2d5.servic[/EMAIL]e: Failed with result 'exit-code'.
```

The gist: udev-configure-printer reports "Failed to fetch Device ID" and then systemd reports "Failed to start Automatic USB/Bluetooth printer setup".  Presumably this is the root of the problem.  /dev/usb/lp0 is not created.

In CUPS, on the web interface, it does not see the printer: Admin -> Find New Printers says "No printers found".

If I add the printer manually (Local Printer, HPLIP) and specify the URI as "usb://Brother/MFC-8220?serial=000J4J171991", and the PPD supplied by Brother (BR8220_2_GPL.ppd), then it adds it OK, but can never contact it (CUPS says "Waiting for printer to become available" forever).

It looks like CUPS is never connecting with the printer, and that it's a USB problem.  The printer's on but idle, and never wakes up (like it would if a print job was submitted, which I do with a test page).

Suggestions would be appreciated!  I am stuck, out of ideas.  Wish this "just worked".[/TD]
[/TR]
[/TABLE]

---

