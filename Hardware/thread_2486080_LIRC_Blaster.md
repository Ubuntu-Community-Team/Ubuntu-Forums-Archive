---
title: "LIRC Blaster"
date: 2023-04-19
forum: Hardware
---

### Post by bon-the-one on 2023-04-19
Hi All,

I recently purchased a USB C IR blaster (for Android phones) in the hope of using it with the type C port on my PC motherboard to control certain local devices. It was a cheap little blaster, from Amazon here : 

[https://www.amazon.com/Universal-Control-Controller-Android-Smartphone/dp/B07B9Z8ZPN/ref=sr_1_2?keywords=ir+blaster+for+android&qid=1681924162&sr=8-2](https://www.amazon.com/Universal-Control-Controller-Android-Smartphone/dp/B07B9Z8ZPN/ref=sr_1_2?keywords=ir+blaster+for+android&qid=1681924162&sr=8-2)

Watching syslog when I connect it, the device is at least detected on the USB bus, thus :
Apr 19 17:19:47 19D-MODEM kernel: [608087.183832] usb 3-2: new full-speed USB device number 4 using xhci_hcd
Apr 19 17:19:48 19D-MODEM kernel: [608087.468630] usb 3-2: New USB device found, idVendor=10c4, idProduct=8468, bcdDevice= 0.00
Apr 19 17:19:48 19D-MODEM kernel: [608087.468640] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Apr 19 17:19:48 19D-MODEM kernel: [608087.468644] usb 3-2: Product: Tview
Apr 19 17:19:48 19D-MODEM kernel: [608087.468647] usb 3-2: Manufacturer: Tiqiaa
Apr 19 17:19:48 19D-MODEM kernel: [608087.472648] usbhid 3-2:1.0: couldn't find an input interrupt endpoint
Apr 19 17:19:48 19D-MODEM mtp-probe: checking bus 3, device 4: "/sys/devices/pci0000:00/0000:00:01.2/0000:07:00.2/0000:08:00.0/0000:09:00.0/usb3/3-2"
Apr 19 17:19:48 19D-MODEM mtp-probe: bus: 3, device: 4 was not an MTP device
Apr 19 17:19:48 19D-MODEM mtp-probe: checking bus 3, device 4: "/sys/devices/pci0000:00/0000:00:01.2/0000:07:00.2/0000:08:00.0/0000:09:00.0/usb3/3-2"
Apr 19 17:19:48 19D-MODEM mtp-probe: bus: 3, device: 4 was not an MTP device
Apr 19 17:19:48 19D-MODEM systemd-udevd[3134588]: 3-2: Process '/usr/lib/snapd/snap-device-helper bind snap_cups_cupsd /devices/pci0000:00/0000:00:01.2/0000:07:00.2/0000:08:00.0/0000:09:00.0/usb3/3-2 189:259' failed with exit code 1.
Apr 19 17:19:48 19D-MODEM systemd-udevd[3134588]: 3-2: Process '/usr/lib/snapd/snap-device-helper bind snap_cups_ippeveprinter /devices/pci0000:00/0000:00:01.2/0000:07:00.2/0000:08:00.0/0000:09:00.0/usb3/3-2 189:259' failed with exit code 1.

If I run an lsusb, the device shows on the bus...
Bus 003 Device 005: ID 10c4:8468 Silicon Labs Tview

However I am not seeing any devices created as /dev/lirc*. I did find a driver on github for the TView Tiqiaa blaster and build it, putting it in lirc/plugins, restarted lircd and replugged the device, but still nothing. 

My lircd.conf is an follows : 
[lircd]
nodaemon        = False
driver          = devinput
device          = auto
output          = /var/run/lirc/lircd
pidfile         = /var/run/lirc/lircd.pid
plugindir       = /usr/lib/x86_64-linux-gnu/lirc/plugins
permission      = 666
allow-simulate  = No
repeat-max      = 600
#effective-user =
#listen         = [address:]port
#connect        = host[:port]
#loglevel       = 6
#release        = true
#release_suffix = _EVUP
#logfile        = ...
#driver-options = ...


[lircmd]
uinput          = False
nodaemon        = False

Does anyone have any suggestions on how I might get this simple device working on Ubuntu? Any experience with it?

Would really appreciate the help. All I want to be able to do is send simple commands to my aquarium lighting controller to automate the lighting routines,

Many thanks in advance,

Bon

---

