---
title: "Trying to mount FS on via FTDI device"
date: 2011-01-04
forum: Hardware
---

### Post by rjr162 on 2011-01-04
Hello,

I'm running Ubuntu 10.10 x86. Some of the devices I use for my work require flashing from a webpage (ActiveX only), so I have Windows XP under VirtualBox. The issue I'm running into is the AX app is saying the module isn't found.

What I've figured it out as it the modules are serial, and plug into the computer's laptop port via USB. The AX app installs the FTDI drivers on the VM, but the VM isn't seeing the device plugged into the USB. I installed the FTDI d2xx drivers from FTDI, but it's still not working.

Here's the dmesg:

[ 1472.592099] usb 3-1: new full speed USB device using uhci_hcd and address 4
[ 1472.797150] ftdi_sio 3-1:1.0: FTDI USB Serial Device converter detected
[ 1472.798161] usb 3-1: FTDI USB Serial Device converter now attached to ttyUSB0


lsusb:

Bus 003 Device 004: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC

lspci:

00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)


My issue is I can't mount the devices. I tried:
none /proc/bus/usb usbdevfs defaults,mode=0666 0 0
as well as using usbfs instead of usbdevfs

The issue I'm currently running into is mount says both usbfs and usbdevfs are unknown file types.

Edit> I just thought I'd add in something I noticed.. in VBox's settings, for the USB Filters it does list ADS WebUpdater blah blah, so it appears VBox is seeing it, but for some reason the ActiveX app within the VBox is saying no cable plugged in (it's not finding the unit). I guess this may be more a question for the VBox guys and the USB aspect, or it does need to be mounted (not sure, but that's what the FTDI readme says for the linux drivers)

---

