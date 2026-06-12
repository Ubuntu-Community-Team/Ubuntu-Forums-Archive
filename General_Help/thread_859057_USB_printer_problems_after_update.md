---
title: "USB printer problems after update"
date: 2008-07-14
forum: General Help
---

### Post by phiaward on 2008-07-14
A couple of days ago, I installed some updates through the Update Manager. I don't remember the names of them - I think there were 5 or 6 packages. Yesterday, I tried to print something. Up until this point, I've had no problems printing anything. Then I go the message that the printer (Epson Stylus C45) was not connected. I tested the cable, turned the printer off and on, unplugged it and plugged it back in to the mains, etc. Nothing helped. I tried dmesg | grep -i usb and this is what it gave me after turning the printer off and on:
>  dmesg | grep -i usb
[   50.206296] usbcore: registered new interface driver usbfs
[   50.206318] usbcore: registered new interface driver hub
[   50.222237] usbcore: registered new device driver usb
[   50.255656] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   50.256465] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   50.312295] usb usb1: configuration #1 chosen from 1 choice
[   50.312319] hub 1-0:1.0: USB hub found
[   50.414867] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   50.426060] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   50.426175] usb usb2: configuration #1 chosen from 1 choice
[   50.426204] hub 2-0:1.0: USB hub found
[   51.565127] usb 2-2: new high speed USB device using ehci_hcd and address 3
[   51.677038] usb 2-2: device descriptor read/64, error -71
[   51.892884] usb 2-2: device descriptor read/64, error -71
[   52.108692] usb 2-2: new high speed USB device using ehci_hcd and address 4
[   52.220608] usb 2-2: device descriptor read/64, error -71
[   52.436436] usb 2-2: device descriptor read/64, error -71
[   52.652276] usb 2-2: new high speed USB device using ehci_hcd and address 5
[   52.675000] usb 2-2: device descriptor read/8, error -71
[   52.795786] usb 2-2: device descriptor read/8, error -71
[   53.007976] usb 2-2: new high speed USB device using ehci_hcd and address 6
[   53.030737] usb 2-2: device descriptor read/8, error -71
[   53.152023] usb 2-2: device descriptor read/8, error -71
[   54.167048] usb 1-1: new full speed USB device using ohci_hcd and address 2
[   54.386262] usb 1-1: configuration #1 chosen from 1 choice
[   54.690728] usb 1-3: new low speed USB device using ohci_hcd and address 3
[   54.893862] usb 1-3: configuration #1 chosen from 1 choice
[   55.198229] usb 1-4: new full speed USB device using ohci_hcd and address 4
[   56.034998] usb 1-4: configuration #1 chosen from 1 choice
[   56.341307] usb 1-10: new low speed USB device using ohci_hcd and address 5
[   56.557589] usb 1-10: configuration #1 chosen from 1 choice
[   69.143421] usbcore: registered new interface driver usbserial
[   69.143446] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[   69.143493] usbcore: registered new interface driver usbserial_generic
[   69.143495] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[   74.810041] usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x04B8 pid 0x0005
[   74.810061] usbcore: registered new interface driver usblp
[   74.983271] usbcore: registered new interface driver hiddev
[   74.993917] input: HID 062a:0001 as /devices/pci0000:00/0000:00:02.0/usb1/1-3/1-3:1.0/input/input3
[   75.002427] input,hidraw0: USB HID v1.10 Mouse [HID 062a:0001] on usb-0000:00:02.0-3
[   75.010050] input: CHESEN USB Keyboard as /devices/pci0000:00/0000:00:02.0/usb1/1-10/1-10:1.0/input/input4
[   75.018395] input,hidraw1: USB HID v1.10 Keyboard [CHESEN USB Keyboard] on usb-0000:00:02.0-10
[   75.030905] input: CHESEN USB Keyboard as /devices/pci0000:00/0000:00:02.0/usb1/1-10/1-10:1.1/input/input5
[   75.034448] input,hidraw2: USB HID v1.10 Device [CHESEN USB Keyboard] on usb-0000:00:02.0-10
[   75.034464] usbcore: registered new interface driver usbhid
[   75.034468] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   75.043811] pwc: Logitech QuickCam Orbit/Sphere USB webcam detected.
[   75.051194] usbcore: registered new interface driver Philips webcam
[   75.415817] usbcore: registered new interface driver snd-usb-audio
[  110.128671] usb 2-2: new high speed USB device using ehci_hcd and address 10
[  110.240652] usb 2-2: device descriptor read/64, error -71
[  110.456551] usb 2-2: device descriptor read/64, error -71
[  110.672484] usb 2-2: new high speed USB device using ehci_hcd and address 11
[  110.784449] usb 2-2: device descriptor read/64, error -71
[  111.000384] usb 2-2: device descriptor read/64, error -71
[  111.216319] usb 2-2: new high speed USB device using ehci_hcd and address 12
[  111.239829] usb 2-2: device descriptor read/8, error -71
[  111.358244] usb 2-2: device descriptor read/8, error -71
[  111.572221] usb 2-2: new high speed USB device using ehci_hcd and address 13
[  111.596191] usb 2-2: device descriptor read/8, error -71
[  111.718852] usb 2-2: device descriptor read/8, error -71
[49631.421856] usb 2-2: new high speed USB device using ehci_hcd and address 14
[49631.537776] usb 2-2: device descriptor read/64, error -71
[49631.839372] usb 2-2: configuration #1 chosen from 1 choice
[49632.389176] usb 1-9: new full speed USB device using ohci_hcd and address 6
[49632.569049] usb 1-9: device descriptor read/64, error -62
[49632.852848] usb 1-9: device descriptor read/64, error -62
[49633.132655] usb 1-9: new full speed USB device using ohci_hcd and address 7
[49633.312526] usb 1-9: device descriptor read/64, error -62
[49633.652353] usbcore: registered new interface driver libusual
[49633.689254] Initializing USB Mass Storage driver...
[49633.719262] scsi8 : SCSI emulation for USB Mass Storage devices
[49633.728680] usbcore: registered new interface driver usb-storage
[49633.728687] USB Mass Storage support registered.
[49633.729099] usb-storage: device found at 14
[49633.729101] usb-storage: waiting for device to settle before scanning
[49638.729828] usb-storage: device scan complete
[49638.733686] scsi 8:0:0:0: Direct-Access     SMSC     USB 2 HS-CF      2.50 PQ: 0 ANSI: 0
[49638.737547] scsi 8:0:0:1: Direct-Access     SMSC     USB 2 HS-MS      2.50 PQ: 0 ANSI: 0
[49638.741670] scsi 8:0:0:2: Direct-Access     SMSC     USB 2 HS-SM      2.50 PQ: 0 ANSI: 0
[49638.745292] scsi 8:0:0:3: Direct-Access     SMSC     USB 2 HS-SD/MMC  2.50 PQ: 0 ANSI: 0
[49655.992561] usb 2-9: new high speed USB device using ehci_hcd and address 16
[49656.126923] usb 2-9: configuration #1 chosen from 1 choice
[49656.152914] scsi9 : SCSI emulation for USB Mass Storage devices
[49656.156928] usb-storage: device found at 16
[49656.156933] usb-storage: waiting for device to settle before scanning
[49661.153112] usb-storage: device scan complete
[49662.727827] usb 2-9: reset high speed USB device using ehci_hcd and address 16
[49663.159520] usb 2-9: reset high speed USB device using ehci_hcd and address 16
[49670.286508] usb 2-9: reset high speed USB device using ehci_hcd and address 16
[49817.135295] usb 2-9: USB disconnect, address 16
[50507.940635] usb 1-9: new full speed USB device using ohci_hcd and address 8
[50508.156350] usb 1-9: configuration #1 chosen from 1 choice
[50508.184909] scsi10 : SCSI emulation for USB Mass Storage devices
[50508.185412] usb-storage: device found at 8
[50508.185416] usb-storage: waiting for device to settle before scanning
[50513.182541] usb-storage: device scan complete
[50820.698850] usb 1-9: USB disconnect, address 8
[71610.152085] usb 1-1: USB disconnect, address 2
[71610.152210] usblp0: removed
[71611.494835] usb 1-1: new full speed USB device using ohci_hcd and address 9
[71611.714461] usb 1-1: configuration #1 chosen from 1 choice
[71611.726418] usblp0: USB Bidirectional printer dev 9 if 0 alt 0 proto 2 vid 0x04B8 pid 0x0005

Before I turned the printer off and on, this is what I got:

> [   50.206296] usbcore: registered new interface driver usbfs
[   50.206318] usbcore: registered new interface driver hub
[   50.222237] usbcore: registered new device driver usb
[   50.255656] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   50.256465] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   50.312295] usb usb1: configuration #1 chosen from 1 choice
[   50.312319] hub 1-0:1.0: USB hub found
[   50.414867] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[   50.426060] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   50.426175] usb usb2: configuration #1 chosen from 1 choice
[   50.426204] hub 2-0:1.0: USB hub found
[   51.565127] usb 2-2: new high speed USB device using ehci_hcd and address 3
[   51.677038] usb 2-2: device descriptor read/64, error -71
[   51.892884] usb 2-2: device descriptor read/64, error -71
[   52.108692] usb 2-2: new high speed USB device using ehci_hcd and address 4
[   52.220608] usb 2-2: device descriptor read/64, error -71
[   52.436436] usb 2-2: device descriptor read/64, error -71
[   52.652276] usb 2-2: new high speed USB device using ehci_hcd and address 5
[   52.675000] usb 2-2: device descriptor read/8, error -71
[   52.795786] usb 2-2: device descriptor read/8, error -71
[   53.007976] usb 2-2: new high speed USB device using ehci_hcd and address 6
[   53.030737] usb 2-2: device descriptor read/8, error -71
[   53.152023] usb 2-2: device descriptor read/8, error -71
[   54.167048] usb 1-1: new full speed USB device using ohci_hcd and address 2
[   54.386262] usb 1-1: configuration #1 chosen from 1 choice
[   54.690728] usb 1-3: new low speed USB device using ohci_hcd and address 3
[   54.893862] usb 1-3: configuration #1 chosen from 1 choice
[   55.198229] usb 1-4: new full speed USB device using ohci_hcd and address 4
[   56.034998] usb 1-4: configuration #1 chosen from 1 choice
[   56.341307] usb 1-10: new low speed USB device using ohci_hcd and address 5
[   56.557589] usb 1-10: configuration #1 chosen from 1 choice
[   69.143421] usbcore: registered new interface driver usbserial
[   69.143446] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[   69.143493] usbcore: registered new interface driver usbserial_generic
[   69.143495] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[   74.810041] usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x04B8 pid 0x0005
[   74.810061] usbcore: registered new interface driver usblp
[   74.983271] usbcore: registered new interface driver hiddev
[   74.993917] input: HID 062a:0001 as /devices/pci0000:00/0000:00:02.0/usb1/1-3/1-3:1.0/input/input3
[   75.002427] input,hidraw0: USB HID v1.10 Mouse [HID 062a:0001] on usb-0000:00:02.0-3
[   75.010050] input: CHESEN USB Keyboard as /devices/pci0000:00/0000:00:02.0/usb1/1-10/1-10:1.0/input/input4
[   75.018395] input,hidraw1: USB HID v1.10 Keyboard [CHESEN USB Keyboard] on usb-0000:00:02.0-10
[   75.030905] input: CHESEN USB Keyboard as /devices/pci0000:00/0000:00:02.0/usb1/1-10/1-10:1.1/input/input5
[   75.034448] input,hidraw2: USB HID v1.10 Device [CHESEN USB Keyboard] on usb-0000:00:02.0-10
[   75.034464] usbcore: registered new interface driver usbhid
[   75.034468] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   75.043811] pwc: Logitech QuickCam Orbit/Sphere USB webcam detected.
[   75.051194] usbcore: registered new interface driver Philips webcam
[   75.415817] usbcore: registered new interface driver snd-usb-audio
[  110.128671] usb 2-2: new high speed USB device using ehci_hcd and address 10
[  110.240652] usb 2-2: device descriptor read/64, error -71
[  110.456551] usb 2-2: device descriptor read/64, error -71
[  110.672484] usb 2-2: new high speed USB device using ehci_hcd and address 11
[  110.784449] usb 2-2: device descriptor read/64, error -71
[  111.000384] usb 2-2: device descriptor read/64, error -71
[  111.216319] usb 2-2: new high speed USB device using ehci_hcd and address 12
[  111.239829] usb 2-2: device descriptor read/8, error -71
[  111.358244] usb 2-2: device descriptor read/8, error -71
[  111.572221] usb 2-2: new high speed USB device using ehci_hcd and address 13
[  111.596191] usb 2-2: device descriptor read/8, error -71
[  111.718852] usb 2-2: device descriptor read/8, error -71
[49631.421856] usb 2-2: new high speed USB device using ehci_hcd and address 14
[49631.537776] usb 2-2: device descriptor read/64, error -71
[49631.839372] usb 2-2: configuration #1 chosen from 1 choice
[49632.389176] usb 1-9: new full speed USB device using ohci_hcd and address 6
[49632.569049] usb 1-9: device descriptor read/64, error -62
[49632.852848] usb 1-9: device descriptor read/64, error -62
[49633.132655] usb 1-9: new full speed USB device using ohci_hcd and address 7
[49633.312526] usb 1-9: device descriptor read/64, error -62
[49633.652353] usbcore: registered new interface driver libusual
[49633.689254] Initializing USB Mass Storage driver...
[49633.719262] scsi8 : SCSI emulation for USB Mass Storage devices
[49633.728680] usbcore: registered new interface driver usb-storage
[49633.728687] USB Mass Storage support registered.
[49633.729099] usb-storage: device found at 14
[49633.729101] usb-storage: waiting for device to settle before scanning
[49638.729828] usb-storage: device scan complete
[49638.733686] scsi 8:0:0:0: Direct-Access     SMSC     USB 2 HS-CF      2.50 PQ: 0 ANSI: 0
[49638.737547] scsi 8:0:0:1: Direct-Access     SMSC     USB 2 HS-MS      2.50 PQ: 0 ANSI: 0
[49638.741670] scsi 8:0:0:2: Direct-Access     SMSC     USB 2 HS-SM      2.50 PQ: 0 ANSI: 0
[49638.745292] scsi 8:0:0:3: Direct-Access     SMSC     USB 2 HS-SD/MMC  2.50 PQ: 0 ANSI: 0
[49655.992561] usb 2-9: new high speed USB device using ehci_hcd and address 16
[49656.126923] usb 2-9: configuration #1 chosen from 1 choice
[49656.152914] scsi9 : SCSI emulation for USB Mass Storage devices
[49656.156928] usb-storage: device found at 16
[49656.156933] usb-storage: waiting for device to settle before scanning
[49661.153112] usb-storage: device scan complete
[49662.727827] usb 2-9: reset high speed USB device using ehci_hcd and address 16
[49663.159520] usb 2-9: reset high speed USB device using ehci_hcd and address 16
[49670.286508] usb 2-9: reset high speed USB device using ehci_hcd and address 16
[49817.135295] usb 2-9: USB disconnect, address 16
[50507.940635] usb 1-9: new full speed USB device using ohci_hcd and address 8
[50508.156350] usb 1-9: configuration #1 chosen from 1 choice
[50508.184909] scsi10 : SCSI emulation for USB Mass Storage devices
[50508.185412] usb-storage: device found at 8
[50508.185416] usb-storage: waiting for device to settle before scanning
[50513.182541] usb-storage: device scan complete
[50820.698850] usb 1-9: USB disconnect, address 8
I would appreciate any help. I've also tried deleting the printer through the Gnome interface and when I plug it back it, the GUI recognizes the printer and re-installs it. But when I send a print job, it says the printer is disconnected.

---

### Post by phiaward on 2008-07-14
I found the following message when I looked in the log:
Jul 14 22:16:38 adam-desktop kernel: [  323.565355] audit(1216044998.814:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=13166 profile="/usr/sbin/cupsd" namespace="default"

---

### Post by MarzoRules on 2008-07-14
I don't know if this is any use. I lost my printer recently when I installed my 3G modem. I found this and the printer was working again:

[http://kubuntuforums.net/forums/index.php?topic=3089184.0](http://kubuntuforums.net/forums/index.php?topic=3089184.0)

Maybe it will work for you. Good luck!

---

### Post by Cotopaxi on 2008-07-14
Marzo Rules:

Your Link DOES HELP!! :)

I have been without Printer for 4 weeks (Brother MFC-5440CN) and your link solved in 5 Minutes!

Thank you so much indeed! :popcorn:

---

### Post by Cotopaxi on 2008-07-14
Just to summarize what I changed:

(My system is Kubuntu 8.04 Hardy Heron)

in /etc/udev/rules.d

I opened (with root permission) the file: "40-permissions.rules"

I changed the parragraph "# Printers and Parallel devices":

so it looked like this:


# Printers and Parallel devices
SUBSYSTEM=="printer", OWNER="lp", GROUP="lp"
SUBSYSTEM=="ppdev",         GROUP="lp"
SUBSYSTEM=="usb", KERNEL=="lp[0-9]*", MODE="0660", OWNER="lp", GROUP="lp"


That was the magic tric!

Thanks again for your link!!

---

### Post by phiaward on 2008-07-15
Thanks so much MarzoRules for the link and Cotopaxi for the summary. I am a teacher and I was lost without a printer for a week (fortunately I don't teach comp sci, lol). Anyway, it worked and I am very happy :KS
You know, I had just installed a 3G modem about the time I downloaded the upgrades and lost my printer. The 3G modem may have been the culprit.
Thanks again.

---

