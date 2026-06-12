---
title: "usb bcm203x bluetooth dongle"
date: 2005-11-11
forum: Hardware &amp; Laptops
---

### Post by luk on 2005-11-11
Hi. I have problems with i-Tec bluetooth dongle on Breezy (kernel 2.6.12)
This is this funny one that doesn't have firmware.. (os load firmware to it)

# lsusb
Bus 001 Device 006: ID 0a5c:2033 Broadcom Corp. BCM2033 Bluetooth

I have bluez packages installed.

/usr/share/doc/bluez-utils/README.Debian.gz says:
> Some USB dongles require firmware to make them work: if 2.4 kernel,
install bluez-bcm203x and bluez-firmware.  If 2.6 kernel, just install
bluez-firmware.  The bluez-firmware package is available in Debian's
"non-free" section and also online at
[http://bluez.sourceforge.net/download/debian/](http://bluez.sourceforge.net/download/debian/)


so i 
# dpkg -i bluez-firmware_1.0-1_i386.deb

This doesn't work :(
When I plug dongle syslog shows:

> 
Nov 11 15:55:42 localhost kernel: [4310284.658000] usb 1-1: new full speed USB device using ohci_hcd and address 7
Nov 11 15:55:42 localhost kernel: [4310284.940000] bcm203x: probe of 1-1:1.0 failed with error -5
Nov 11 15:55:43 localhost usb.agent[6716]:      bcm203x: already loaded
Nov 11 15:55:43 localhost usb.agent[6716]:      hci_usb: already loaded
Nov 11 15:55:48 localhost usb.agent[6790]:      bcm203x: already loaded
Nov 11 15:55:48 localhost usb.agent[6790]:      hci_usb: already loaded
Nov 11 15:55:48 localhost usb.agent[6785]:      bcm203x: already loaded
Nov 11 15:55:48 localhost usb.agent[6785]:      hci_usb: already loaded


driver is loaded:
> 
# lsmod |grep bcm
bcm203x                 5956  0
firmware_class         10240  1 bcm203x
usbcore               118204  5 hci_usb,bcm203x,usbhid,ohci_hcd


but still no bluetooth dev is available:
> 
# hcitool dev
Devices:


I know that the dongle is fine and should work under linux, actually I was using it some time ago under fedora..

Anybody know what to do?

---

### Post by ranf on 2005-11-11
[QUOTE=luk]
so i 
# dpkg -i bluez-firmware_1.0-1_i386.deb

This doesn't work 
[/QUOTE]
Post the exact error messages you get.
Maybe you just forgot to put a sudo in front of the dpkg?

---

### Post by luk on 2005-11-12
Package installed fine.
I mean that after installation of bluez-firmware_1.0-1_i386.deb the device still doesn't work..

---

### Post by ranf on 2005-11-13
[QUOTE=luk]Package installed fine.
I mean that after installation of bluez-firmware_1.0-1_i386.deb the device still doesn't work..[/QUOTE]
I see.

Have a look at this:
[http://lists.ubuntulinux.org/archives/ubuntu-users/2004-October/005699.html](http://lists.ubuntulinux.org/archives/ubuntu-users/2004-October/005699.html)

---

### Post by luk on 2005-11-19
Thanks! That helped me :)
Location of firmware was wrong.. (should be in /usr/lib/hotplug/firmware)
One command and my bluetooth is alive again:

> 
root@nx9005:/usr/lib/hotplug/firmware# ln -s /lib/firmware/* ./


---

### Post by cynthiya on 2008-02-13
Bus 001 Device 006: ID 0a5c:2033 Broadcom Corp. BCM2033 Bluetooth



I know that the dongle is fine and should work under linux, actually I was using it some time ago under fedora..

Anybody know what to do?[/QUOTE]

Hi Brother,
could u plz tel me how to configure/use the module in fedora

regs
Cynthiya

---

