---
title: "RESOLVED: rules.d/udev issue [was: scanner stops working after upgrade]"
date: 2017-08-22
forum: Hardware
---

### Post by jrpstonecarver on 2017-08-22
I hope someone can help me. I had 14.04 LTS running for a long time, and everything was fine. I have an ancient Brother ADS-2000 USB scanner that worked perfectly in that older configuration. I know there was some trouble getting it setup, but that was years ago, and I can't find anything about what I had to do way back when.

This morning I upgraded to 16.04 LTS (I know... finally) and everything seems to working except the scanner. Even my network printer still works as it should.

xsane, however, can't find the scanner. The symptom is interesting, though.  When I start xsane I get the message:
[FONT=courier new]
[COLOR=#4b0082]Failed to open device `brother4:bus8;dev1': Invalid argument.[/COLOR][/FONT][COLOR=#4b0082]
[/COLOR]
Classic xsane error from what I can tell, but that bus and device number are wrong. See this:

[COLOR=#4b0082][FONT=courier new]$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 1b1c:1b15 Corsair 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f9:60a0 Brother Industries, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]

As you can see, the scanner is actually on Bus 001, Device 002, not the bus & device reported by xsane's error message.

Run as a regular user, xsane-find-scanner reports:

[COLOR=#4b0082][FONT=courier new]$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.


  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.


could not open USB device 0x1d6b/0x0002 at 002:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0001 at 008:001: Access denied (insufficient permissions)
could not open USB device 0x1b1c/0x1b15 at 007:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0001 at 007:001: Access denied (insufficient permissions)
could not open USB device 0x045e/0x0040 at 006:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0001 at 006:001: Access denied (insufficient permissions)
could not open USB device 0x04f9/0x60a0 at 001:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 001:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0001 at 005:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0001 at 004:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0001 at 003:001: Access denied (insufficient permissions)
  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.


  # Not checking for parallel port scanners.


  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.


  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.[/FONT][/COLOR]

So nothing found. But as root I get a different result:

  [FONT=courier new][COLOR=#4b0082]# sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.


  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.


found USB scanner (vendor=0x04f9, product=0x60a0) at libusb:001:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.


  # Not checking for parallel port scanners.


  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.[/COLOR][/FONT]



And that is right... it's finding the scanner on the proper bus & device numbers.

So... something, somewhere, has the wrong bus & device numbers coded up, and I cannot find it anywhere. I've googled until I am blue in the face. I've looked in config files in a jillion places and can't find anything.

And, of course, if you start xsane as root it has a horrible warning message about how running it as root is REALLY DANGEROUS, but no details on why or what the issues are. So I didn't do that.

I've seen bunches of things online where different devices that were on the computer (and/or their associated drivers) were causing a problem similar to this, but this *worked* with exactly this batch of hardware a couple of days ago. Just fine. The only difference is that I've updated to 16.04 LTS now, and that broke something.

I did go out and get the Brother provided .deb package for scanner support and installed it as well. No change. Current version from the Brother website is: brscan4-0.4.4-3.amd64.deb   Install was fine but doing that made no change.
 
I've also added my user to groups lp, scanner, and saned, thinking that perhaps my user had some permission issue. Again, no difference, even after a full reboot of the system.

I know I will need this scanner to work at some point in the not too distant future. Any advice on how to fix this would be most appreciated. Thank you!

---

### Post by jrpstonecarver on 2017-08-22
Also, for the record, I found a few answers that suggested modifying something in /etc/sane.d, like this thread:

[https://ubuntuforums.org/showthread.php?t=2322206](https://ubuntuforums.org/showthread.php?t=2322206)

so I tried it, by adding this line to the end of /etc/sane.d/dll.conf which is where the "brother4" device name (or backend, or something) comes from:

[COLOR=#4b0082][FONT=courier new]usb 0x04f9 0x60a0[/FONT][/COLOR]

That made no difference at all, even after a full reboot to restart everything, just in case.

I am completely at a loss for where the wrong bus and device numbers are being stored, and I would be delighted if anyone could point me in any sort of useful direction.

Again, thank you!

---

### Post by jrpstonecarver on 2017-08-22
And another item... just because I am trying to be thorough. I can see the scanner details when I look. Everything is properly connected via USB...

[FONT=courier new][COLOR=#4b0082]# lsusb -D /dev/bus/usb/001/002[/COLOR][/FONT][FONT=courier new][COLOR=#4b0082]/dev/bus/usb/001/002[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]root@zaphod:~# lsusb -D /dev/bus/usb/001/002[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]Device: ID 04f9:60a0 Brother Industries, Ltd [/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]Device Descriptor:[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]  bLength                18[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]  bDescriptorType         1[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]  bcdUSB               2.00[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]  bDeviceClass            0 (Defined at Interface level)[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]  bDeviceSubClass         0 [/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]  bDeviceProtocol         0 [/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]  bMaxPacketSize0        64[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]  idVendor           0x04f9 Brother Industries, Ltd[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]  idProduct          0x60a0 [/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]  bcdDevice            1.00[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]  iManufacturer           0 [/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]  iProduct                0 [/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]  iSerial                 3 U63287F2G130855[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]  bNumConfigurations      1[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]  Configuration Descriptor:[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]    bLength                 9[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]    bDescriptorType         2[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]    wTotalLength           92[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]    bNumInterfaces          3[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]    bConfigurationValue     1[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]    iConfiguration          0 [/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]    bmAttributes         0xc0[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]      Self Powered[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]    MaxPower                2mA[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]    Interface Descriptor:[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]      bLength                 9[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]      bDescriptorType         4[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]      bInterfaceNumber        0[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]      bAlternateSetting       0[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]      bNumEndpoints           2[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]      bInterfaceClass       255 Vendor Specific Class[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]      bInterfaceSubClass    255 Vendor Specific Subclass[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]      bInterfaceProtocol    255 Vendor Specific Protocol[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]      iInterface              0 [/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]      Endpoint Descriptor:[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        bLength                 7[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        bDescriptorType         5[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        bEndpointAddress     0x01  EP 1 OUT[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        bmAttributes            2[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]          Transfer Type            Bulk[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]          Synch Type               None[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]          Usage Type               Data[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        wMaxPacketSize     0x0200  1x 512 bytes[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        bInterval               1[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]      Endpoint Descriptor:[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        bLength                 7[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        bDescriptorType         5[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        bEndpointAddress     0x82  EP 2 IN[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        bmAttributes            2[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]          Transfer Type            Bulk[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]          Synch Type               None[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]          Usage Type               Data[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        wMaxPacketSize     0x0200  1x 512 bytes[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        bInterval               1[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]    Interface Descriptor:[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]      bLength                 9[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]      bDescriptorType         4[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]      bInterfaceNumber        1[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]      bAlternateSetting       0[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]      bNumEndpoints           3[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]      bInterfaceClass       255 Vendor Specific Class[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]      bInterfaceSubClass    255 Vendor Specific Subclass[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]      bInterfaceProtocol    255 Vendor Specific Protocol[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]      iInterface              0 [/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]      Endpoint Descriptor:[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        bLength                 7[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        bDescriptorType         5[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        bEndpointAddress     0x04  EP 4 OUT[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        bmAttributes            2[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]          Transfer Type            Bulk[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]          Synch Type               None[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]          Usage Type               Data[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        wMaxPacketSize     0x0200  1x 512 bytes[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        bInterval               1[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]      Endpoint Descriptor:[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        bLength                 7[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        bDescriptorType         5[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        bEndpointAddress     0x85  EP 5 IN[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        bmAttributes            2[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]          Transfer Type            Bulk[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]          Synch Type               None[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]          Usage Type               Data[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        wMaxPacketSize     0x0200  1x 512 bytes[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        bInterval               1[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]      Endpoint Descriptor:[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        bLength                 7[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        bDescriptorType         5[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        bEndpointAddress     0x89  EP 9 IN[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        bmAttributes            3[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]          Transfer Type            Interrupt[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]          Synch Type               None[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]          Usage Type               Data[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        wMaxPacketSize     0x0008  1x 8 bytes[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        bInterval              16[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]    Interface Descriptor:[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]      bLength                 9[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]      bDescriptorType         4[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]      bInterfaceNumber        2[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]      bAlternateSetting       0[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]      bNumEndpoints           3[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]      bInterfaceClass       255 Vendor Specific Class[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]      bInterfaceSubClass    255 Vendor Specific Subclass[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]      bInterfaceProtocol    255 Vendor Specific Protocol[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]      iInterface              0 [/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]      Endpoint Descriptor:[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        bLength                 7[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        bDescriptorType         5[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        bEndpointAddress     0x07  EP 7 OUT[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        bmAttributes            2[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]          Transfer Type            Bulk[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]          Synch Type               None[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]          Usage Type               Data[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        wMaxPacketSize     0x0200  1x 512 bytes[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        bInterval               1[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]      Endpoint Descriptor:[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        bLength                 7[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        bDescriptorType         5[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        bEndpointAddress     0x88  EP 8 IN[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        bmAttributes            2[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]          Transfer Type            Bulk[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]          Synch Type               None[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]          Usage Type               Data[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        wMaxPacketSize     0x0200  1x 512 bytes[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        bInterval               1[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]      Endpoint Descriptor:[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        bLength                 7[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        bDescriptorType         5[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        bEndpointAddress     0x89  EP 9 IN[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        bmAttributes            3[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]          Transfer Type            Interrupt[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]          Synch Type               None[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]          Usage Type               Data[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        wMaxPacketSize     0x0008  1x 8 bytes[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]        bInterval              16[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]Device Qualifier (for other device speed):[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]  bLength                10[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]  bDescriptorType         6[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]  bcdUSB               2.00[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]  bDeviceClass            0 (Defined at Interface level)[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]  bDeviceSubClass         0 [/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]  bDeviceProtocol         0 [/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]  bMaxPacketSize0        64[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]  bNumConfigurations      1[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]Device Status:     0x0001[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]  Self Powered[/COLOR][/FONT]

---

### Post by jrpstonecarver on 2017-08-27
I have made a tiny bit of progress, but this is not yet resolved. Still looking for any help I can get.

I continued googling and eventually - despite doing everything I thought was needed before - I tried changing the permissions on the proper device.  Apparently, there is a permissions problem.  So, right now, after many plug/unplug sequences, I have this:
[FONT=courier new][COLOR=#4b0082]
$ lsusb
[/COLOR][/FONT][FONT=courier new][COLOR=#4b0082]Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]Bus 007 Device 002: ID 1b1c:1b15 Corsair [/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]Bus 006 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]Bus 001 Device 009: ID 04f9:60a0 Brother Industries, Ltd [/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/COLOR][/FONT]

So the scanner is currently on bus 1, device 009.

Then I run the following as root:

[FONT=courier new][COLOR=#4b0082]# ls -l /dev/bus/usb/001/009
[/COLOR][/FONT][FONT=courier new][COLOR=#4b0082]crw-rw-r-- 1 root root 189, 8 Aug 27 11:21 009[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]#  chmod a+rw /dev/bus/usb/001/009[/COLOR][/FONT]

[FONT=courier new][COLOR=#4b0082]# ls -l /dev/bus/usb/001/009
[/COLOR][/FONT][FONT=courier new][COLOR=#4b0082]crw-rw-rw- 1 root root 189, 8 Aug 27 11:21 009[/COLOR][/FONT]

so now everyone has write permission to that device. Then, back as a regular user:
[COLOR=#4b0082][FONT=&quot]$ sane-find-scanner[/FONT][/COLOR]
[COLOR=#4b0082][FONT=&quot]
[/FONT][/COLOR]
[COLOR=#4b0082][FONT=&quot]  # sane-find-scanner will now attempt to detect your scanner. If the[/FONT][/COLOR]
[COLOR=#4b0082][FONT=&quot]  # result is different from what you expected, first make sure your[/FONT][/COLOR]
[COLOR=#4b0082][FONT=&quot]  # scanner is powered up and properly connected to your computer.[/FONT][/COLOR]
[COLOR=#4b0082][FONT=&quot]
[/FONT][/COLOR]
[COLOR=#4b0082][FONT=&quot]  # No SCSI scanners found. If you expected something different, make sure that[/FONT][/COLOR]
[COLOR=#4b0082][FONT=&quot]  # you have loaded a kernel SCSI driver for your SCSI adapter.[/FONT][/COLOR]
[COLOR=#4b0082][FONT=&quot]
[/FONT][/COLOR]
[COLOR=#4b0082][FONT=&quot]could not open USB device 0x1d6b/0x0002 at 002:001: Access denied (insufficient permissions)[/FONT][/COLOR]
[COLOR=#4b0082][FONT=&quot]could not open USB device 0x1d6b/0x0001 at 008:001: Access denied (insufficient permissions)[/FONT][/COLOR]
[COLOR=#4b0082][FONT=&quot]could not open USB device 0x1b1c/0x1b15 at 007:002: Access denied (insufficient permissions)[/FONT][/COLOR]
[COLOR=#4b0082][FONT=&quot]could not open USB device 0x1d6b/0x0001 at 007:001: Access denied (insufficient permissions)[/FONT][/COLOR]
[COLOR=#4b0082][FONT=&quot]could not open USB device 0x045e/0x0040 at 006:002: Access denied (insufficient permissions)[/FONT][/COLOR]
[COLOR=#4b0082][FONT=&quot]could not open USB device 0x1d6b/0x0001 at 006:001: Access denied (insufficient permissions)[/FONT][/COLOR]
[COLOR=#ff0000]**[FONT=&quot]found USB scanner (vendor=0x04f9, product=0x60a0) at libusb:001:009[/FONT]**[/COLOR]
[FONT=courier new][COLOR=#4b0082]could not open USB device 0x1d6b/0x0002 at 001:001: Access denied (insufficient permissions)[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]could not open USB device 0x1d6b/0x0001 at 005:001: Access denied (insufficient permissions)[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]could not open USB device 0x1d6b/0x0001 at 004:001: Access denied (insufficient permissions)[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]could not open USB device 0x1d6b/0x0001 at 003:001: Access denied (insufficient permissions)[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]  # Your USB scanner was (probably) detected. It may or may not be supported by[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]  # SANE. Try scanimage -L and read the backend's manpage.[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]
  # Not checking for parallel port scanners.

[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]  # Most Scanners connected to the parallel port or other proprietary ports[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]  # can't be detected by this program.[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]
[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]  # You may want to run this program as root to find all devices. Once you[/COLOR][/FONT]
[FONT=courier new][COLOR=#4b0082]  # found the scanner devices, be sure to adjust access permissions as[/COLOR][/FONT]
[COLOR=#4b0082][FONT=courier new]  # necessary.[/FONT]
[/COLOR]
And there we see (in bold red) that the scanner is found, on the proper bus & device. Good. And xsane starts and finds the scanner.

So, problem solved, except that if I unplug the scanner or reboot, the permissions change is lost.

That lead me down into the mysteries of udev, and I am lost.

I read and read and tried a bunch of things. Eventually it appeared that I need to create an entry in a rules file in /etc/udev/rules.d to set the permissions on the scanner as I want when it is detected.

I created a file named [COLOR=#4b0082][FONT=courier new]/etc/udev/rules.d/71-sane.rules[/FONT][/COLOR] and put many different entries in it, but none of them seemed to set the permissions properly. Here are a number of the entries I tried in that file:

[COLOR=#4b0082][FONT=courier new]ATTRS{idVendor}=="0x04f9", ATTRS{idProduct}=="0x60a0", MODE="0666", GROUP="scanner"
SUBSYSTEM=="usb", ATTRS{idVendor}=="0x04f9", ATTRS{idProduct}=="0x60a0", MODE="0666", GROUP="scanner"
SUBSYSTEM=="usb", ATTRS{idVendor}=="0x04f9", ATTRS{idProduct}=="0x60a0", MODE="0666", GROUP="scanner", ENV{libsane_matched}="yes"[/FONT][/COLOR]

Note that each of those entries was tried on its own in the [COLOR=#4b0082][FONT=courier new]71-sane.rules[/FONT][/COLOR] file, and there was a reboot and/or a [FONT=courier new][COLOR=#4b0082]udevadm control --reload[/COLOR][/FONT] executed before each attempt.

None of those entries resulted in the permissions of the proper device being changed when I looked.  And yes, I would unplug and plug the scanner back in to force the execution of the rule after the reboot or reload.

Can anyone tell me what I am doing wrong with the rules file that is keeping the permissions from changing? I think if I can fix that, this problem will be solved permanently.

Thank you!

---

### Post by jrpstonecarver on 2017-08-27
Changing the subject. The previous post explains how I got to that point, but still need help fixing a device permissions issue permanently.

---

### Post by jrpstonecarver on 2017-08-27
This has been resolved now.  Turns out that various places that show syntax for udev rules files get it wrong. Here's the line that worked:

SUBSYSTEM=="usb", ATTRS{idVendor}=="04f9", ATTRS{idProduct}=="60a0", MODE="0666", GROUP="scanner", ENV{libsane_matched}="yes"

The only change from one of the lines that didn't work was removing the leading "0x" from the Vendor and Product IDs.

Once that change was made, the scanner is found as a regular user, and it works.

Why this is not solved in a general way in 16.04 is beyond me. I am pretty sure that stuff like this is what keeps (or kept... maybe it is too late) Linux from taking over the desktop.

Anyway, this item is resolved now.

---

