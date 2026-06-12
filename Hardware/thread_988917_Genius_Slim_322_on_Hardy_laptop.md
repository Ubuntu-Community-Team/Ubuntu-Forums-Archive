---
title: "Genius Slim 322 on Hardy laptop"
date: 2008-11-21
forum: Hardware
---

### Post by purefan on 2008-11-21
Hello guys!

I searched the forums for "slim 322" and nothing showed up so thought it was worth posting a new thread.

Here goes the same old "my webcam doesnt work", but I have tried many things and found what I think is the reason for it to fail.

After understanding a little how hardware detection works on ubuntu I learned that the webcam -being a usb one- was actually being added as "usb6", while camorama's error message said that it couldnt connect to /dev/video0

So I turned to udevmonitor and here is what it showed me:
> 
UEVENT[1227247289.297974] add      /devices/pci0000:00/0000:00:13.5/usb6/6-1 (usb)
UEVENT[1227247289.299127] add      /devices/pci0000:00/0000:00:13.5/usb6/6-1/usb_endpoint/usbdev6.8_ep00 (usb_endpoint)
UEVENT[1227247289.299188] add      /devices/pci0000:00/0000:00:13.5/usb6/6-1/6-1:1.0 (usb)
UEVENT[1227247289.299208] add      /devices/pci0000:00/0000:00:13.5/usb6/6-1/6-1:1.0/usb_endpoint/usbdev6.8_ep81 (usb_endpoint)
UEVENT[1227247289.299228] add      /devices/pci0000:00/0000:00:13.5/usb6/6-1/6-1:1.0/usb_endpoint/usbdev6.8_ep82 (usb_endpoint)
UEVENT[1227247289.299248] add      /devices/pci0000:00/0000:00:13.5/usb6/6-1/6-1:1.0/usb_endpoint/usbdev6.8_ep83 (usb_endpoint)
UDEV  [1227247289.303352] add      /devices/pci0000:00/0000:00:13.5/usb6/6-1 (usb)
UDEV  [1227247289.306993] add      /devices/pci0000:00/0000:00:13.5/usb6/6-1/usb_endpoint/usbdev6.8_ep00 (usb_endpoint)
UDEV  [1227247289.376186] add      /devices/pci0000:00/0000:00:13.5/usb6/6-1/6-1:1.0 (usb)
UDEV  [1227247289.381273] add      /devices/pci0000:00/0000:00:13.5/usb6/6-1/6-1:1.0/usb_endpoint/usbdev6.8_ep81 (usb_endpoint)
UDEV  [1227247289.384731] add      /devices/pci0000:00/0000:00:13.5/usb6/6-1/6-1:1.0/usb_endpoint/usbdev6.8_ep82 (usb_endpoint)
UDEV  [1227247289.388726] add      /devices/pci0000:00/0000:00:13.5/usb6/6-1/6-1:1.0/usb_endpoint/usbdev6.8_ep83 (usb_endpoint)


now there is a /dev/video0 so please correct me if im wrong but shouldnt camorama look for the device on usb6 rather than video0?

Thanks for your time!

---

