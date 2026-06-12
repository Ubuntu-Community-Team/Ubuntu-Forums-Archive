---
title: "USB device now takes 90 seconds to access"
date: 2013-06-06
forum: Hardware
---

### Post by ee4hire on 2013-06-06
I've been using the Atmel AVR ISP mkII on my fully  up to date 12.04 LTS machine for some time. I use avrdude (standard apt-get install) to program Atmel devices. I hadn't used it for a few weeks and when I started it up this week, it fails to connect to the device for about 90 seconds. I issue a command from the command line and the command blocks for very close to 90 seconds but then proceeds to talk to the device and program it. I've checked the AVR ISP mkII on my MacBook Pro using avrdude from Mac Ports and it works with no delay as usual. It appears that something has changed in my Ubuntu setup.
I do use a udev rule so I can operate this programmer as a regular user, but running with sudo made no difference.

Any ideas what has gone wrong or what needs to be fixed? Should I file a bug?

Here is syslog from a run that worked, i.e. programmed properly, but including the ~90 second delay before starting:
Jun  6 11:17:01 upland CRON[19430]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun  6 11:28:28 upland kernel: [238726.768134] usb 5-2: new full-speed USB device number 46 using ohci_hcd
Jun  6 11:28:43 upland kernel: [238741.904137] usb 5-2: device descriptor read/64, error -110
Jun  6 11:28:58 upland kernel: [238757.144134] usb 5-2: device descriptor read/64, error -110
Jun  6 11:28:59 upland kernel: [238757.384135] usb 5-2: new full-speed USB device number 47 using ohci_hcd
Jun  6 11:29:14 upland kernel: [238772.520136] usb 5-2: device descriptor read/64, error -110
Jun  6 11:29:29 upland kernel: [238787.760138] usb 5-2: device descriptor read/64, error -110
Jun  6 11:29:29 upland kernel: [238788.000138] usb 5-2: new full-speed USB device number 48 using ohci_hcd
Jun  6 11:29:40 upland kernel: [238798.408124] usb 5-2: device not accepting address 48, error -110
Jun  6 11:29:40 upland kernel: [238798.544133] usb 5-2: new full-speed USB device number 49 using ohci_hcd
Jun  6 11:29:50 upland kernel: [238808.952138] usb 5-2: device not accepting address 49, error -110
Jun  6 11:29:50 upland kernel: [238808.952165] hub 5-0:1.0: unable to enumerate USB device on port 2
Jun  6 11:30:11 upland kernel: [238829.456584] usb 1-4.4: reset full-speed USB device number 17 using ehci_hcd

Also, here is the output of "sudo -v lsusb -d 03eb:
Bus 001 Device 017: ID 03eb:2104 Atmel Corp. AVR ISP mkII
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        16
  idVendor           0x03eb Atmel Corp.
  idProduct          0x2104 AVR ISP mkII
  bcdDevice            2.00
  iManufacturer           1 ATMEL
  iProduct                2 AVRISP mkII
  iSerial                 3 000200053768
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0
    bmAttributes         0xc0
      Self Powered
    MaxPower              100mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0
      bInterfaceProtocol      0
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              10
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              10
Device Status:     0x0001
  Self Powered

---

### Post by ee4hire on 2013-06-06
Found the problem, it was autosuspend. By setting the device's autosuspend setting to 1, no longer have the issue. Not sure which upgrade changed the default behavior in 12.04, but now need to add a script to udev so I can use this device.

---

