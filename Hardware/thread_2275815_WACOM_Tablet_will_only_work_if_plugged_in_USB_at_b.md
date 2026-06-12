---
title: "WACOM Tablet will only work if plugged in USB at boot time"
date: 2015-04-28
forum: Hardware
---

### Post by bloozguy on 2015-04-28
This is on UBUNTU 14.04 LTS

If I plug my WACOM (Intuos4 PTK-440) into USB AFTER I boot or if I unplug and replug, without booting, the tablet does not respond.

YET I do get :

(lsusb) Bus 003 Device 016: ID 056a:00b8 Wacom Co., Ltd Intuos4 4x6

(dmesg) [234491.960080] usb 3-1: new full-speed USB device number 16 using xhci_hcd [234492.088883] usb 3-1: New USB device found, idVendor=056a, idProduct=00b8 [234492.088889] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0 [234492.088892] usb 3-1: Product: PTK-440 [234492.088895] usb 3-1: Manufacturer: Tablet [234492.089936] input: Wacom Intuos4 4x6 as /devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0/input/input28

(In /dev/input/by-id) :

usb-Tablet_PTK-440-event-mouse

usb-Tablet_PTK-440-mouse

Furthermore GIMP "sees" it (eraser,pad,stylus and cursor)

If I reboot with the tablet plugged into USB it all works.

What am I missing? Really puzzled.

---

