---
title: "How to execute script on device insertion?"
date: 2008-12-31
forum: Hardware
---

### Post by BaringForgeone on 2008-12-31
I have a couple of things I want to automate on my Ubuntu rig.  The first, when I insert my Verizon 3g card, I want to automagically bring up gnome-ppp and do the dial-up.  How/where do I hook my ppp/dial script into the udevd/hotplug system?

The other thing I want to do, along the same lines, is when a CD is inserted, I want to automatically rip and save off, then eject the cd.  

I read through the [https://wiki.ubuntu.com/Hardware/Detection](https://wiki.ubuntu.com/Hardware/Detection) wiki, which talks about some netlink socket, and a new udevd environment, but doesn't give any further guidance on how to rig that up.  Any advice on how to wire this up?

Thanks,
Tom


uname -a output:
Linux tom-laptop 2.6.24-22-generic #1 SMP Mon Nov 24 19:35:06 UTC 2008 x86_64 GNU/Linux


dmesg output when verizon 3g device is plugged in:
[ 3796.446609] usb-storage: device found at 2
[ 3796.446614] usb-storage: waiting for device to settle before scanning
[ 3796.485459] usbcore: registered new interface driver usbserial
[ 3796.485651] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[ 3796.485892] usbcore: registered new interface driver usbserial_generic
[ 3796.485896] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[ 3796.495961] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for GSM modem (1-port)
[ 3796.496003] option 6-2:1.0: GSM modem (1-port) converter detected
[ 3796.496116] usb 6-2: GSM modem (1-port) converter now attached to ttyUSB0
[ 3796.496126] option 6-2:1.1: GSM modem (1-port) converter detected
[ 3796.496192] usb 6-2: GSM modem (1-port) converter now attached to ttyUSB1
[ 3796.496202] option 6-2:1.2: GSM modem (1-port) converter detected
[ 3796.496259] usb 6-2: GSM modem (1-port) converter now attached to ttyUSB2
[ 3796.496268] option 6-2:1.3: GSM modem (1-port) converter detected
[ 3796.496324] usb 6-2: GSM modem (1-port) converter now attached to ttyUSB3
[ 3796.496333] usbcore: registered new interface driver option
[ 3796.496335] /build/buildd/linux-2.6.24/drivers/usb/serial/option.c: USB Driver for GSM modems: v0.7.1
[ 3796.512000] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for airprime
[ 3796.512037] usbcore: registered new interface driver airprime
[ 3797.019449] usb-storage: device scan complete
[ 3797.022404] scsi 28:0:0:0: Direct-Access     Novatel  MMC Storage      2.31 PQ: 0 ANSI: 2
[ 3797.028407] sd 28:0:0:0: [sde] Attached SCSI removable disk
[ 3797.028449] sd 28:0:0:0: Attached scsi generic sg5 type 0
[ 3842.649218] input: Virtual ThinkFinger Keyboard as /devices/virtual/input/input14
[ 3847.447935] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[ 3847.447941] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[ 3847.447944] pcmcia: see [http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html](http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html) for details.

---

### Post by sdennie on 2008-12-31
This guide should give you all the information you need to do both those things.  [http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html).

---

