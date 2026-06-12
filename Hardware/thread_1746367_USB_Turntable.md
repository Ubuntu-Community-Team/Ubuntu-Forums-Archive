---
title: "USB Turntable"
date: 2011-05-01
forum: Hardware
---

### Post by TedinOz on 2011-05-01
I was gifted a USB Turntable Recorder. The unit come with built in Windows and Mac auto recognition but nothing happens in Ubuntu when I connect the USB. A disc is provided to install Audacity through either Windows or Mac. I already have Audacity but until I can connect the unit via USB, Audacity doesn't recognise it. I'm thinking I need to somehow install a driver. The unit is recognised when I connect the USB as per Syslog...

[HTML]May  1 19:40:58 ted-Satellite-L300 kernel: [ 4573.776066] usb 5-2: new full speed USB device using uhci_hcd and address 7
May  1 19:40:58 ted-Satellite-L300 kernel: [ 4573.992824] input: USB Audio Controller as /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.3/input/input14
May  1 19:40:58 ted-Satellite-L300 kernel: [ 4573.993099] generic-usb 0003:0C76:1605.0006: input,hidraw1: USB HID v1.00 Device [USB Audio Controller] on usb-0000:00:1d.0-2/input3
May  1 19:40:59 ted-Satellite-L300 rtkit-daemon[1679]: Successfully made thread 5536 of process 3381 (n/a) owned by '1000' RT at priority 5.
May  1 19:40:59 ted-Satellite-L300 rtkit-daemon[1679]: Supervising 4 threads of 1 processes of 1 users.
May  1 19:40:59 ted-Satellite-L300 rtkit-daemon[1679]: Successfully made thread 5537 of process 3381 (n/a) owned by '1000' RT at priority 5.
May  1 19:40:59 ted-Satellite-L300 rtkit-daemon[1679]: Supervising 5 threads of 1 processes of 1 users.
[/HTML]

I am hoping from the info here that it is possible to run a command and have the unit installed and recognised. Can anyone help with this please?

---

### Post by grahammechanical on 2011-05-01
Have you tried Sound Preferences to see if the USB turntable is listed as an audio device? It has to show up somewhere.

Regards.

---

### Post by TedinOz on 2011-05-01
> **grahammechanical said:**
> Have you tried Sound Preferences to see if the USB turntable is listed as an audio device? It has to show up somewhere.

Regards.

Thanks but no luck there. At this point I don't think it will show up anywhere until it is installed as an application with a driver and that is what I don't know how to do.

---

### Post by TedinOz on 2011-05-02
A bump...:)

---

### Post by TedinOz on 2011-05-10
This fixed itself when I returned to Maverick.

---

