---
title: "How do I blacklist devices from being created?"
date: 2008-06-11
forum: Hardware
---

### Post by MetalgodZ on 2008-06-11
I'm using a Sprint/Nextel Novatel Ovation U727 wireless broadband stick, and I've gotten the device to nicely auto-detect with the airprime module, however the first thing it detects is a "cdrom" device:

[quote=/var/log/messages]Jun 11 15:48:50 linuxtest kernel: [  364.282487] usb 4-1: new full speed USB device using uhci_hcd and address 2
Jun 11 15:48:50 linuxtest kernel: [  364.449561] usb 4-1: configuration #1 chosen from 1 choice
Jun 11 15:48:50 linuxtest kernel: [  364.541964] usbcore: registered new interface driver libusual
Jun 11 15:48:50 linuxtest kernel: [  364.579370] Initializing USB Mass Storage driver...
Jun 11 15:48:50 linuxtest kernel: [  364.580797] scsi4 : SCSI emulation for USB Mass Storage devices
Jun 11 15:48:50 linuxtest kernel: [  364.582125] usbcore: registered new interface driver usb-storage
Jun 11 15:48:50 linuxtest kernel: [  364.582136] USB Mass Storage support registered.
Jun 11 15:48:55 linuxtest kernel: [  369.584786] scsi 4:0:0:0: CD-ROM            Novatel  Mass Storage     1.00 PQ: 0 ANSI: 2
Jun 11 15:48:55 linuxtest kernel: [  369.617740] sr1: scsi-1 drive
Jun 11 15:48:55 linuxtest kernel: [  369.617916] sr 4:0:0:0: Attached scsi generic sg2 type 5[/quote]

This is where the device detection stops, and the system auto-mounts the Windows installation "cdrom" that's included in the device...Helpful for Windows, but not so much for Ubuntu. Running "lsscsi" shows that in addition to the /dev/sg2 device, there is another (emulated) CDROM device that's been added. To allow the device to continue and the /dev/ttyUSB<#> portions to be recognized, I must eject /dev/sg2, which also removes an additional SCSI CDROM device. After doing this, the system immediately recognizes the "modem" portion of the card:
[quote=/var/log/messages]Jun 11 15:48:59 linuxtest kernel: [  373.010078] usb 4-1: new full speed USB device using uhci_hcd and address 3
Jun 11 15:48:59 linuxtest kernel: [  373.176041] usb 4-1: configuration #1 chosen from 1 choice
Jun 11 15:48:59 linuxtest kernel: [  373.178940] usbserial_generic 4-1:1.0: airprime converter detected
Jun 11 15:48:59 linuxtest kernel: [  373.179113] usb 4-1: airprime converter now attached to ttyUSB0
Jun 11 15:48:59 linuxtest kernel: [  373.179194] usb 4-1: airprime converter now attached to ttyUSB1
Jun 11 15:48:59 linuxtest kernel: [  373.179271] usb 4-1: airprime converter now attached to ttyUSB2
Jun 11 15:48:59 linuxtest kernel: [  373.182063] usbserial_generic 4-1:1.1: airprime converter detected
Jun 11 15:48:59 linuxtest kernel: [  373.182180] usb 4-1: airprime converter now attached to ttyUSB3
Jun 11 15:48:59 linuxtest kernel: [  373.182259] usb 4-1: airprime converter now attached to ttyUSB4
Jun 11 15:48:59 linuxtest kernel: [  373.182341] usb 4-1: airprime converter now attached to ttyUSB5
Jun 11 15:48:59 linuxtest kernel: [  373.184026] usbserial_generic 4-1:1.2: airprime converter detected
Jun 11 15:48:59 linuxtest kernel: [  373.184157] usb 4-1: airprime converter now attached to ttyUSB6
Jun 11 15:48:59 linuxtest kernel: [  373.184241] usb 4-1: airprime converter now attached to ttyUSB7
Jun 11 15:48:59 linuxtest kernel: [  373.184332] usb 4-1: airprime converter now attached to ttyUSB8
Jun 11 15:48:59 linuxtest kernel: [  373.186049] usbserial_generic 4-1:1.3: airprime converter detected
Jun 11 15:48:59 linuxtest kernel: [  373.186184] usb 4-1: airprime converter now attached to ttyUSB9
Jun 11 15:48:59 linuxtest kernel: [  373.186268] usb 4-1: airprime converter now attached to ttyUSB10
Jun 11 15:48:59 linuxtest kernel: [  373.186361] usb 4-1: airprime converter now attached to ttyUSB11
Jun 11 15:48:59 linuxtest kernel: [  373.188030] usbserial_generic 4-1:1.4: airprime converter detected
Jun 11 15:48:59 linuxtest kernel: [  373.188192] usb 4-1: airprime converter now attached to ttyUSB12
Jun 11 15:48:59 linuxtest kernel: [  373.188285] usb 4-1: airprime converter now attached to ttyUSB13
Jun 11 15:48:59 linuxtest kernel: [  373.188377] usb 4-1: airprime converter now attached to ttyUSB14
Jun 11 15:48:59 linuxtest kernel: [  373.408940] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for GSM modem (1-port)
Jun 11 15:48:59 linuxtest kernel: [  373.409379] usbcore: registered new interface driver option
Jun 11 15:48:59 linuxtest kernel: [  373.409386] /build/buildd/linux-2.6.24/drivers/usb/serial/option.c: USB Driver for GSM modems: v0.7.1[/quote]

I can easily eject the device manually and then start pppd to allow internet access, however I'd like to make this as automatic as possible, starting with preventing /dev/sg2 from being pulled in, allowing the detection of the /dev/ttyUSB<#> devices to continue.

How would I go about blacklisting this?

---

