---
title: "Permission denied counldn't open USB device."
date: 2012-03-11
forum: Hardware
---

### Post by Matt Pellegrini on 2012-03-11
The problem:

matt@Laptop:/dev\> freenect-glview
Kinect camera test
Number of devices found: 1
libusb couldn't open USB device /dev/bus/usb/002/035: Permission denied.
libusb requires write access to USB device nodes.
Could not open motor: -3
Could not open device

So I tried to fix this by having the owning group of the device as the group kinect, of which user matt is a member.

udevadm -a -n /dev/bus/usb/002/035 gives :

 looking at device '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5.2':
    KERNEL=="2-1.5.2"
    SUBSYSTEM=="usb"
    DRIVER=="usb"
    ATTR{configuration}==""
    ATTR{bNumInterfaces}==" 1"
    ATTR{bConfigurationValue}=="1"
    ATTR{bmAttributes}=="c0"
    ATTR{bMaxPower}=="100mA"
    ATTR{urbnum}=="12"
    ATTR{idVendor}=="045e"
    ATTR{idProduct}=="02b0"
    ATTR{bcdDevice}=="0105"
    ATTR{bDeviceClass}=="00"
    ATTR{bDeviceSubClass}=="00"
    ATTR{bDeviceProtocol}=="00"
    ATTR{bNumConfigurations}=="1"
    ATTR{bMaxPacketSize0}=="64"
    ATTR{speed}=="12"
    ATTR{busnum}=="2"
    ATTR{devnum}=="35"
    ATTR{devpath}=="1.5.2"
    ATTR{version}==" 2.00"
    ATTR{maxchild}=="0"
    ATTR{quirks}=="0x0"
    ATTR{avoid_reset_quirk}=="0"
    ATTR{authorized}=="1"
    ATTR{manufacturer}=="Microsoft"
    ATTR{product}=="Xbox NUI Motor"

So I added a rule under /etc/udev/rules.d/my-rules.rules

# Kinect
SUBSYSTEM=="usb",ATTR{product}=="Xbox NUI Motor",Name="kinect_motor",Group="kinect"

and still get the same error message,

any ideas?

thanks in advance,
Matt

EDIT: 
note:  I have tried logging out and in again after adding myself to the group and did udevadm control --reload-rules.

---

