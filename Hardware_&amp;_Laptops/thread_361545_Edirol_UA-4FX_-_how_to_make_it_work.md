---
title: "Edirol UA-4FX - how to make it work?"
date: 2007-02-14
forum: Hardware &amp; Laptops
---

### Post by dunder on 2007-02-14
lsusb gives me:
> Bus 002 Device 003: ID 0582:00a3 Roland Corp. 

dmesg gives:
> [17179671.808000] usb 2-2: new full speed USB device using uhci_hcd and address 3
[17179671.992000] usb 2-2: configuration #1 chosen from 1 choice

syslog gives:
> Feb 14 20:23:51 localhost kernel: [17179671.808000] usb 2-2: new full speed USB device using uhci_hcd and address 3
Feb 14 20:23:51 localhost kernel: [17179671.992000] usb 2-2: configuration #1 chosen from 1 choice
Feb 14 20:23:52 localhost NetworkManager: <debug info>^I[1171481032.035072] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_582_a3_noserial'). 
Feb 14 20:23:52 localhost NetworkManager: <debug info>^I[1171481032.093661] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_582_a3_noserial_if0'). 
Feb 14 20:23:52 localhost NetworkManager: <debug info>^I[1171481032.201014] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_582_a3_noserial_if1'). 
Feb 14 20:23:52 localhost NetworkManager: <debug info>^I[1171481032.333411] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_582_a3_noserial_if2'). 
Feb 14 20:23:52 localhost NetworkManager: <debug info>^I[1171481032.401509] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_582_a3_noserial_usbraw'). 

and /proc/asound/cards gives me nothing after loading module snd_usb_audio ...

EDIT:
**Problem solved ... "Advanced Driver" switch placed on the left side of interface should be "Off". After switching it, ALSA found USB audio device and it works on linux without any problems :)**

---

### Post by lucasa on 2007-11-29
Did Linux recognize the midi usb interface?
Have you gotten some xruns?
Thank's.
Lucas, from Brazil

---

