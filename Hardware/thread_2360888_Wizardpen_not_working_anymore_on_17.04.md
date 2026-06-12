---
title: "Wizardpen not working anymore on 17.04"
date: 2017-05-09
forum: Hardware
---

### Post by alexan on 2017-05-09
My old "UC-Logic Technology Corp. Tablet WP5540U" (as named in lsusb) doesn't work on Lubuntu 17.04.


On natively 17.04: it doesn't work
in virtual machine on the same OS: 16.04 live (running on 17.04 as host) == wizardpen works.
in virtual machine on the same OS, but 17.04 live (17.04 live running on the 17.04 host) wizardpen doesn't work.

---

### Post by QIII on 2017-05-09
Hello!

What does "doesn't work" mean?

---

### Post by alexan on 2017-05-09
> **QIII said:**
> Hello!

What does "doesn't work" mean?

Boot 17.04 and log in the desktop and in terminal run this: **lsusb |grep -i tablet**. Then I got

Bus 003 Device 003: ID 5543:0004 UC-Logic Technology Corp. Tablet WP5540U


Move the pen = no sign of life (the mouse cursors is suppoed to move). press pen buttons = no sign of life.

Open **xev**: move pen and press its buttons.. no sign of life.



Open Vitualbox: run 16.04 live distro and pass the usb tablet: tablet is recognized and everything works
Close and open in Virtualbox the 17.04 live distro: tablet tablet is recognized and still stay dead.









dmsg when plug the tablet in the native 17.04 (not working)
> [ 1728.633302] usb 3-7: new low-speed USB device number 5 using xhci_hcd
[ 1728.780205] usb 3-7: New USB device found, idVendor=5543, idProduct=0004
[ 1728.780207] usb 3-7: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 1728.780207] usb 3-7: Product: Tablet WP5540U
[ 1728.780208] usb 3-7: Manufacturer: UC-LOGIC
[ 1728.793217] input: UC-LOGIC Tablet WP5540U Pen as /devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7:1.0/0003:5543:0004.0006/input/input18
[ 1728.849380] input: UC-LOGIC Tablet WP5540U Mouse as /devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7:1.0/0003:5543:0004.0006/input/input19
[ 1728.849435] uclogic 0003:5543:0004.0006: input,hidraw1: USB HID v1.00 Mouse [UC-LOGIC Tablet WP5540U] on usb-0000:00:14.0-7/input0


the pen as Virtualbox guest in 16.04 live (working)
> [  900.295368] usb 2-2: USB disconnect, device number 3
[ 1160.766223] usb 2-2: new full-speed USB device number 4 using ohci-pci
[ 1161.046451] usb 2-2: New USB device found, idVendor=5543, idProduct=0004
[ 1161.046455] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 1161.046456] usb 2-2: Product: Tablet WP5540U
[ 1161.046458] usb 2-2: Manufacturer: UC-LOGIC


the pen as Virtualbox guest in 17.04 live (not working)
> [   40.671925] usb 2-2: new full-speed USB device number 4 using ohci-pci
[   40.988555] usb 2-2: New USB device found, idVendor=5543, idProduct=0004
[   40.988557] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[   40.988558] usb 2-2: Product: Tablet WP5540U
[   40.988559] usb 2-2: Manufacturer: UC-LOGIC
[   41.018279] input: UC-LOGIC Tablet WP5540U Pen as /devices/pci0000:00/0000:00:06.0/usb2/2-2/2-2:1.0/0003:5543:0004.0003/input/input10
[   41.083362] input: UC-LOGIC Tablet WP5540U Mouse as /devices/pci0000:00/0000:00:06.0/usb2/2-2/2-2:1.0/0003:5543:0004.0003/input/input11
[   41.083432] uclogic 0003:5543:0004.0003: input,hidraw1: USB HID v1.00 Mouse [UC-LOGIC Tablet WP5540U] on usb-0000:00:06.0-2/input0

---

### Post by alexan on 2017-05-10
I've issued a bug here: [https://bugs.launchpad.net/wizardpen/+bug/1689755](https://bugs.launchpad.net/wizardpen/+bug/1689755)

the problem seems to be related to the switch from evdev (up to 16.04) to libinput (16.10 and beyond): to proof this theory I need to switch back libinput to evdev in 17.04: anyone know if that's possible?

(just removing libinput package render the system unusable with all input device disabled)

---

