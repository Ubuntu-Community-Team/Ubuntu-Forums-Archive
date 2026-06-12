---
title: "cp210x failed to get vendor val 0x370b"
date: 2017-10-04
forum: Hardware
---

### Post by rdmapes on 2017-10-04
Good Day,
I have an Icom R2500 that I had working on Ubuntu. It's been some time since I've used it. The other day I decided to do some SWL. No Go. I get the following...

I see that the kernel can see the device, knows what it is.
kernel: [ 1044.208053] usb 1-4.3.1.2: new full-speed USB device number 8 using ehci-pci
kernel: [ 1044.330167] usb 1-4.3.1.2: New USB device found, idVendor=10c4, idProduct=ea60
kernel: [ 1044.330169] usb 1-4.3.1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
kernel: [ 1044.330171] usb 1-4.3.1.2: Product: CP2101 USB to UART Bridge Controller
kernel: [ 1044.330173] usb 1-4.3.1.2: Manufacturer: Silicon Labs
kernel: [ 1044.330174] usb 1-4.3.1.2: SerialNumber: IC-R2500 0501405
mtp-probe: checking bus 1, device 7: "/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4.3/1-4.3.1/1-4.3.1.1"
mtp-probe: bus: 1, device: 7 was not an MTP device
mtp-probe: checking bus 1, device 8: "/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4.3/1-4.3.1/1-4.3.1.2"
mtp-probe: bus: 1, device: 8 was not an MTP device
kernel: [ 1046.256297] usbcore: registered new interface driver cp210x
kernel: [ 1046.256316] usbserial: USB Serial support registered for cp210x
kernel: [ 1046.256366] cp210x 1-4.3.1.2:1.0: cp210x converter detected
kernel: [ 1046.257467] cp210x 1-4.3.1.2:1.0: failed to get vendor val 0x370b size 1: -32
kernel: [ 1046.257484] cp210x: probe of 1-4.3.1.2:1.0 failed with error -5

lsusb gives me this...

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0d8c:013c C-Media Electronics, Inc. CM108 Audio Controller
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID modinfo is there...0458:0024 KYE Systems Corp. (Mouse Systems) 
Bus 001 Device 005: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Bus 001 Device 020: ID 10c4:ea60 Cygnal Integrated Products, Inc. CP210x UART Bridge / myAVR mySmartUSB light
Bus 001 Device 019: ID 08bb:2901 Texas Instruments PCM2901 Audio Codec
Bus 001 Device 018: ID 0424:2502 Standard Microsystems Corp. 
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 002: ID 04b3:4485 IBM Corp. Serial Converter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

modinfo usbserial
filename:       /lib/modules/4.10.0-35-generic/kernel/drivers/usb/serial/usbserial.ko
license:        GPL
description:    USB Serial Driver core
author:         Greg Kroah-Hartman <gregkh@linuxfoundation.org>
srcversion:     CD8657734C582FCA9894D9B
depends:        
intree:         Y
vermagic:       4.10.0-35-generic SMP mod_unload 
parm:           vendor:User specified USB idVendor (ushort)
parm:           product:User specified USB idProduct (ushort)


Ubuntu sees the device, loads up the driver. Complains about the vendor and will not give an ID. Not sure why. Worked for many years. But, somewhere an upgrade buggered things up. Anyone worked through this one?
In the mean time I'll comb the forum to see what's out there.

---

### Post by rdmapes on 2017-10-06
Good Evening,
I've been out there on the WWW to see what I can see. So far not much has been found. The kernel gets the correct vendor ID and product ID. Identifies the manufacturer correctly. But, the system stumbles when it gets to here.

kernel: [ 1046.257467] cp210x 1-4.3.1.2:1.0: failed to get vendor val 0x370b size 1: -32
kernel: [ 1046.257484] cp210x: probe of 1-4.3.1.2:1.0 failed with error -5

I've been searching to see what a "vendor val" is. Not have much luck finding out that that is. Different than the vendor ID. If anyone can explain that line to me I would greatly appreciate it.

Regards,

---

### Post by rdmapes on 2017-10-08
Good Day,
Reloaded the laptop (Lenovo T61p) with Unbuntu 16.04. Found that kernel Ubuntu, with Linux 4.10.0-35-generic was buggered for this usb device. After learning that I know that I didn't need to reload the laptop; Ha!. Either way I have a clean install now. Set grub to boot on kernel Ubuntu, with Linux 4.8.0-36-generic. All is now well.

The fun begins as I work through configuring wine and the Icom app to work. Usually works out, but each pc acts a bit different.

Enjoy,

---

### Post by paulnotpaul on 2017-10-27
Oh man I'm running into the same exact issue you are. Except I REALLLLY don't want to reformat :(. I have a CP210x device and I get the same error you do on a 4.10.0-37 kernel. It used to work on an older install. 

c210x 1-6.1:1.0: failed to get vendor val 0x370b size 1: -32

It then doesn't get attached to a tty. GRRRRS.  Did you figure out any reason why?

Thanks!

---

