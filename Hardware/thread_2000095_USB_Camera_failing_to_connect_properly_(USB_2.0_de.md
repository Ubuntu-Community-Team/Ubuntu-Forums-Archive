---
title: "USB Camera failing to connect properly (USB 2.0 device detected as USB 3.0 ??)"
date: 2012-06-09
forum: Hardware
---

### Post by seanbow on 2012-06-09
I am trying to connect a Point Grey Chameleon USB camera to my laptop (Asus G55VW) running Ubuntu 10.04 32 bit, but it fails. I believe that the problem is that Ubuntu is trying to connect to it as if it were USB 3 capable, but it's only a USB 2 device.

The bizarre thing is that I have two identical laptops (hardware, BIOS version, OS version) and it connects properly on one of the laptops.

On connecting to the laptop where it functions correctly, on connecting the following is logged by the kernel

```
[14098.152899] usb 2-1.4: new high speed USB device using ehci_hcd and address 54
[14098.254729] usb 2-1.4: configuration #1 chosen from 1 choice
```

When disconnecting the camera, the following is logged

```
[14204.899516] usb 2-1.4: USB disconnect, address 54
```

Now, for the broken laptop, the following is logged when connecting

```
[  526.377943] usb 3-4: new high speed USB device using xhci_hcd and address 0
[  526.401381] xhci_hcd 0000:00:14.0: WARN: short transfer on control ep
[  526.404363] xhci_hcd 0000:00:14.0: WARN: short transfer on control ep
[  526.407269] xhci_hcd 0000:00:14.0: WARN: short transfer on control ep
[  526.410192] xhci_hcd 0000:00:14.0: WARN: short transfer on control ep
[  526.410354] usb 3-4: configuration #1 chosen from 1 choice
```

When trying to stream data, the following errors are logged

```

[  756.360909] xhci_hcd 0000:00:14.0: ERROR no room on ep ring
[  756.360917] usb 3-4: usbfs: usb_submit_urb returned -12
[  756.364254] xhci_hcd 0000:00:14.0: ERROR no room on ep ring
[  756.364259] usb 3-4: usbfs: usb_submit_urb returned -12
[  756.367581] xhci_hcd 0000:00:14.0: ERROR no room on ep ring
[  756.367585] usb 3-4: usbfs: usb_submit_urb returned -12
[  756.370908] xhci_hcd 0000:00:14.0: ERROR no room on ep ring
[  756.370922] usb 3-4: usbfs: usb_submit_urb returned -12
```

And when disconnecting, I get

```
[ 724.452737] usb 3-4: USB disconnect, address 5
```

I've spent hours googling and trying to fix this without any success. I've reinstalled Ubuntu numerous times... Killing xhci in an attempt to force ehci with sudo modprobe -r xhci just results in no USB devices being recognized whatsoever (including my mouse).

I've also tried installing Ubuntu 11.04 and 12.04 with equal results.

When the camera is connected to the broken laptop, the entry given for it with lsusb -t reads

```
|__ Port 2: Dev 8, If 0, Class=vend., Driver=, 480M
```

and the entry for the camera within the output of lsusb -v is

```
Bus 003 Device 008: ID 1e10:2005  
 Device Descriptor:
   bLength                18
   bDescriptorType         1
   bcdUSB               2.00
   bDeviceClass            0 (Defined at Interface level)
   bDeviceSubClass         0 
   bDeviceProtocol         0 
   bMaxPacketSize0        64
   idVendor           0x1e10 
   idProduct          0x2005 
   bcdDevice            0.03
   iManufacturer           1 Point Grey Research
   iProduct                2 USB 2.0 Digital Imaging Camera
   iSerial                 3 00B7E70A
   bNumConfigurations      1
   Configuration Descriptor:
     bLength                 9
     bDescriptorType         2
     wTotalLength           25
     bNumInterfaces          1
     bConfigurationValue     1
     iConfiguration          0 
     bmAttributes         0x80
       (Bus Powered)
     MaxPower              500mA
     Interface Descriptor:
       bLength                 9
       bDescriptorType         4
       bInterfaceNumber        0
       bAlternateSetting       0
       bNumEndpoints           1
       bInterfaceClass       255 Vendor Specific Class
       bInterfaceSubClass      0 
       bInterfaceProtocol      0 
       iInterface              0 
       Endpoint Descriptor:
         bLength                 7
         bDescriptorType         5
         bEndpointAddress     0x81  EP 1 IN
         bmAttributes            2
           Transfer Type            Bulk
           Synch Type               None
           Usage Type               Data
         wMaxPacketSize     0x0200  1x 512 bytes
         bInterval               0
 Device Qualifier (for other device speed):
   bLength                10
   bDescriptorType         6
   bcdUSB               2.00
   bDeviceClass            0 (Defined at Interface level)
   bDeviceSubClass         0 
   bDeviceProtocol         0 
   bMaxPacketSize0        64
   bNumConfigurations      1
 Device Status:     0x0000
   (Bus Powered)
```

---

