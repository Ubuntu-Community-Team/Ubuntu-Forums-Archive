---
title: "USB to Serial"
date: 2011-01-28
forum: Hardware
---

### Post by daniel333 on 2011-01-28
Hey everyone, 

More or less very new to Linux here. I have to manage some Cisco switches using a USB-to-Serial device. Initially this worked PERFECTLY! They showed as /dev/ttyUSB0 and /dev/ttyUSB1. 

I added another USB-to-Serial to manage a third device then things fell apart. I removed the devices and rebooted. When I insert the first device, it works great. But when I insert the second, it never detects. 

What I tried
1) Removing all devices, rebooting. And inserting them one by one while on
2) Installed devices while the machine was off

I booted up another Ubuntu PC I had here and managed to handle what needed to be done, but eventually ran into the same problem. 

Any ideas on where to start here?

My OS
n@danielnix-lt:/sys/bus/usb/devices/1-8$ uname --all
Linux danielnix-lt 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux

Dmesg output. You can see the first one, always works. Second one, not. 
[   59.220359] usb 1-8.4: new full speed USB device using ehci_hcd and address 6
[   59.311211] usb 1-8.4: configuration #1 chosen from 1 choice
[   59.358829] usbcore: registered new interface driver usbserial
[   59.361840] USB Serial support registered for generic
[   59.362108] usbcore: registered new interface driver usbserial_generic
[   59.362117] usbserial: USB Serial Driver core
[   59.373989] USB Serial support registered for pl2303
[   59.374726] pl2303 1-8.4:1.0: pl2303 converter detected
[   59.379067] usb 1-8.4: pl2303 converter now attached to ttyUSB0
[   59.379142] usbcore: registered new interface driver pl2303
[   59.379150] pl2303: Prolific PL2303 USB to serial adaptor driver
[   75.012338] usb 1-8.1: new full speed USB device using ehci_hcd and address 7
[   75.105141] usb 1-8.1: unable to read config index 0 descriptor/all
[   75.105153] usb 1-8.1: can't read configurations, error -32
[   75.176381] usb 1-8.1: new full speed USB device using ehci_hcd and address 8
[   75.268937] usb 1-8.1: unable to read config index 0 descriptor/all
[   75.268949] usb 1-8.1: can't read configurations, error -32
[   75.340416] usb 1-8.1: new full speed USB device using ehci_hcd and address 9
[   75.361263] usb 1-8.1: unable to read config index 0 descriptor/all
[   75.361274] usb 1-8.1: can't read configurations, error -32
[   75.432379] usb 1-8.1: new full speed USB device using ehci_hcd and address 10
[   75.453216] usb 1-8.1: unable to read config index 0 descriptor/all
[   75.453228] usb 1-8.1: can't read configurations, error -32
[   75.453589] hub 1-8:1.0: unable to enumerate USB device on port 1


so far enjoying Ubuntu, hope I can work through this stumbling point. 

Thanks in advance, 
-Daniel

---

### Post by tgalati4 on 2011-01-28
Find an old PC with a real serial port.  Load an Ubuntu LiveCD, see if you can talk to the device.  It's possible that the device you want to talk to is having hardware problems.

Also, the PL2303 converter doesn't work with all serial devices.  Certain devices require synchronous serial port communication.  USB is hotplug and asynchronous.  So any device expecting uninterrupted communication via serial port will not appreciate USB interrupts.

---

### Post by daniel333 on 2011-01-28
Thanks for the quick reply. I am still new to Linux (honestly I took a Linux class in 2002 and haven't really used it since). Please forgive any off questions. 

> **tgalati4 said:**
> Find an old PC with a real serial port.  Load an Ubuntu LiveCD, see if you can talk to the device.  

Unusably slow, but worked. 

> **tgalati4 said:**
> 
It's possible that the device you want to talk to is having hardware problems.

I don't know, I have my doubts as these were be managed with multiple serial/USB adapters under XP for weeks. Also they work the first time under Ubuntu, until I need to change physical interfaces. 


> **tgalati4 said:**
> 
Also, the PL2303 converter doesn't work with all serial devices.  Certain devices require synchronous serial port communication.  USB is hotplug and asynchronous.  So any device expecting uninterrupted communication via serial port will not appreciate USB interrupts.
Good info. Ill keep that in mind. Thanks for elaborating. 


Just for fun I reinstalled Ubuntu (BLAZING fast install, love it!) they worked great. BUT once again after rebooting and moving the ports around after a bit of work. It is no longer detecting anything but the first device I plug in. 

Reinstalled again, working great. I am not moving ANYTHING. 

Any other ideas? 

I get the feeling based on those error messages that there is some sort of config file that is created I need to delete or rebuild. But I just don't have the knowledge to track it down.

---

