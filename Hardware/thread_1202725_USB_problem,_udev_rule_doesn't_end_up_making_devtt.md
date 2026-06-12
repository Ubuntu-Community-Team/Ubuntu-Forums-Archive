---
title: "USB problem, udev rule doesn't end up making /dev/ttyUSB0 for Huey colorimeter"
date: 2009-07-02
forum: Hardware
---

### Post by Cracauer on 2009-07-02
I must be doing something easy wrong.

I have udev rules to turn my USB device into /dev/ttyUSB0. I made sure I have the USB vendor and product id correct.  Still, all I get is
```

usb 4-1: USB disconnect, address 10
usb 4-1: new low speed USB device using uhci_hcd and address 11
usb 4-1: configuration #1 chosen from 1 choice

```

No /dev/ entries become available, neither in the usb directory nor the expected ttyUSB entries.

%%

Long story:

Huey Colorimter.  This thing is supposed to be used as a USB serial device.  The Debian package with the application to use it is argyll.  The package installs udev rules as follows:
```

#Enable serial port connected instruments on USB serial converted connected on first two ports.
KERNEL=="ttyUSB[01]", MODE="666"
[...]
# Huey
SYSFS{idVendor}=="0971", SYSFS{idProduct}=="2005", MODE="666"
--- end of file ---

% lsusb | grep 0971
Bus 004 Device 011: ID 0971:2005 Gretag-Macbeth AG 

```

I used the original Debian package entry and I tried copy'n'pasting one from the argyll website.  udev and hald were restarted on package install.  I restarted udev several times and unplugged and replugged the device several times.

Still, I get no /dev entry and the kernel only says:
```

usb 4-1: USB disconnect, address 10
usb 4-1: new low speed USB device using uhci_hcd and address 11
usb 4-1: configuration #1 chosen from 1 choice

```

I have manually loaded the generic usb serial driver module. Maybe I need another one?

%%

I have seen the in past kernels (2.6.24) people were preventing the usb_hid driver from grabbing this device by blacklisting it in that driver.  But that doesn't seem to be required or even supported under 2.6.28 anymore.

Any idea what I am doing wrong? What else can I try?

If I need to blacklist in the new kernel, too, how do I do that now that HID_QUIRK_IGNORE is gone?

%%

Anybody else here having of these? Care to share your `lsmod`?

---

