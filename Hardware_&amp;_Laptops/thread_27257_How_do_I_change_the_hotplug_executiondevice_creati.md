---
title: "How do I change the hotplug execution/device creation order?"
date: 2005-04-15
forum: Hardware &amp; Laptops
---

### Post by Remix_88 on 2005-04-15
Hi, 
 
I have installed Synce and Multisync along with all the extra bits and bobs and everything works via USB, but only if I run 'sudo synce-serial-start' manually. Hotplug can't start pppd and from the logs below the problem appears to be that udev is creating the /dev/ttyUSB0 *after* hotplug has called 'synce-serial-start'. Therefore pppd fails because the device it is being asked to connect to doesn't exist.  
 
Any dea how I can change the execution order so that udev can create the device before the call to 'synce-serial-start'? I have been sucessful in connecting to and MultiSyncing with iPAQ 3970, iPAQ 4150 an Orange SPV C500 Windows Mobile Smart Phone and Evolution 2.2.1.1. 

I have been keeping good notes and fully intend to submit a detailed HOWTO article next week, but would love to get the auto connection working first. Thanks in advance for any assistance. 
 
```
Apr 15 16:03:43 localhost kernel: usb 1-1: new full speed USB device using uhci_hcd and address 7 
Apr 15 16:03:44 localhost kernel: usb 1-1: configuration #1 chosen from 3 choices 
Apr 15 16:03:44 localhost usb.agent[8938]: Keeping default configuration with /sys//devices/pci0000:00/0000:00:1d.0/usb1/1-1 
Apr 15 16:03:44 localhost kernel: drivers/usb/serial/usb-serial.c: USB Serial support registered for Generic 
Apr 15 16:03:44 localhost kernel: usbcore: registered new driver usbserial_generic 
Apr 15 16:03:44 localhost kernel: usbcore: registered new driver usbserial 
Apr 15 16:03:44 localhost kernel: drivers/usb/serial/usb-serial.c: USB Serial Driver core v2.0 
Apr 15 16:03:44 localhost kernel: drivers/usb/serial/usb-serial.c: USB Serial support registered for PocketPC PDA 
Apr 15 16:03:44 localhost kernel: drivers/usb/serial/ipaq.c: USB PocketPC PDA driver v0.5 
Apr 15 16:03:44 localhost kernel: ipaq 1-1:1.0: PocketPC PDA converter detected 
Apr 15 16:03:44 localhost usb.agent[8950]: ipaq: loaded successfully 
Apr 15 16:03:44 localhost kernel: usb 1-1: PocketPC PDA converter now attached to ttyUSB0 
Apr 15 16:03:44 localhost kernel: usbcore: registered new driver ipaq 
Apr 15 16:03:44 localhost synce-serial-start: Executing '/usr/sbin/pppd call synce-device' 
Apr 15 16:03:44 localhost pppd[9105]: In file /etc/ppp/peers/synce-device: unrecognized option '/dev/ttyUSB0' 
Apr 15 16:03:44 localhost udev[9118]: creating device node '/dev/ttyUSB0'
```

---

### Post by hamiltonlight on 2005-07-03
Hi there,

Can you tell me how you got the C500 to sync? Mine has not been backed up since I've moved to Ubuntu full time.

Regards,

Hamilton

---

### Post by Remix_88 on 2005-07-18
I will post a HOWTO soon.

---

### Post by Shabba on 2005-10-18
Did you ever get round to that howto mate? I'd love to use my C500 via linux but only to copy mp3's to and from it not sync email etc..

---

### Post by xsence on 2005-10-25
[QUOTE=Remix_88]I will post a HOWTO soon.[/QUOTE]

hi, have you posted the howto already?

thanks in advance

---

