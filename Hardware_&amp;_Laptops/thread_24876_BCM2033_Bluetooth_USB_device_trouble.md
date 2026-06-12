---
title: "BCM2033 Bluetooth USB device trouble"
date: 2005-04-08
forum: Hardware &amp; Laptops
---

### Post by krist on 2005-04-08
Hi,

I can't get my Broadcom BCM2033 Bluetooth USB device to work. It seems like the firmware cannot be transferred to the device. This is from syslog:

Apr  8 20:43:45 localhost usb.agent[9830]:      bcm203x: loaded successfully
Apr  8 20:43:45 localhost usb.agent[9808]:      bcm203x: loaded successfully
Apr  8 20:43:45 localhost usb.agent[9841]:      bcm203x: loaded successfully
Apr  8 20:43:45 localhost kernel: bcm203x_probe: Mini driver request failed
Apr  8 20:43:45 localhost kernel: bcm203x: probe of 1-2:1.0 failed with error -5
Apr  8 20:43:45 localhost kernel: usbcore: registered new driver bcm203x

No hci device is being registered, so no userspace bt apps work. I have installed bluez-firmware from Debian unstable non-free, the firmware is located at:

/lib/firmware/BCM2033-FW.bin
/lib/firmware/BCM2033-MD.hex

bluez-pin + bluez-utils are also installed and I'm using the Hoary stock 686 kernel. Any ideas?


Greetings,
krist

---

### Post by krist on 2005-04-09
Found the problem, you need [bluez-bcm203x](http://packages.ubuntu.com/hoary/admin/bluez-bcm203x) from universe to be installed.

---

### Post by ripley on 2005-06-30
To resolve the same problem i've added this lines to /etc/hotplug/usb/bcm203x
hotplug script (present in the deb package bluez-bcm203x) :

export DEVICE
export ACTION

before the line that exec /usr/lib/bluez-bcm203x/bcm203x.

That environment variables are needed by the application to know how to
upload the firmware (the kernel support to the firmware upload don't work
in this kernel versions [2.6.10/11])

---

