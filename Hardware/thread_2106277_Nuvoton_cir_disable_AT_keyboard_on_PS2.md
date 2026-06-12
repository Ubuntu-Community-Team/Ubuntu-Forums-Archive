---
title: "Nuvoton_cir disable AT keyboard on PS2"
date: 2013-01-18
forum: Hardware
---

### Post by bobrenard on 2013-01-18
Hello,
 When I plug a Nuvoton_cir on my motherboard (asrock H61M-ITX with ubuntu 11.10 or ubuntu 12.04) my** AT keyboard plugged in ps2 port is disabled**.
The remote mce works and i can select entry in xbmc or mythtv.
 The mouse works


 to make AT keyboard ok the only workaround is to reboot after unplug Nuvoton_cir from motherboard...

If I use an usb keyboard , it works.

 I have tried to re-install all with 12.04 and** even in the installation phase keyboard is disabled  if nuvoton_cir is plugged**.


  This is an extract of dmesg :
**with plugged Nuvoton w836x7hg : AT keyboard not active**

 [    0.536735] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.536739] ACPI: Power Button [PWRB]
[    0.536772] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.536774] ACPI: Power Button [PWRF]
[    1.072843] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[   12.337749] input: Nuvoton w836x7hg Infrared Remote Transceiver as /devices/pnp0/00:09/rc/rc0/input3
[   12.337821] rc0: Nuvoton w836x7hg Infrared Remote Transceiver as /devices/pnp0/00:09/rc/rc0
[   12.342798] nuvoton_cir: driver has been successfully loaded
[   12.350470] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/input/input4
[   12.350614] generic-usb 0003:046D:C016.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.0-1.4/input0
[   12.350642] usbcore: registered new interface driver usbhid
[   12.350644] usbhid: USB HID core driver
[   12.351509] input: MCE IR Keyboard/Mouse (nuvoton-cir) as /devices/virtual/input/input5
[   12.352050] IR MCE Keyboard/mouse protocol handler initialized
[   12.359937] lirc_dev: IR Remote Control driver registered, major 249
[   12.360442] rc rc0: lirc_dev: driver ir-lirc-codec (nuvoton-cir) registered at minor = 0
[   12.360444] IR LIRC bridge handler initialized
[   12.780869] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6


 **Without Nuvoton w836x7hg : AT keyboard works !!!!**
 [    0.532749] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.532752] ACPI: Power Button [PWRB]
[    0.532786] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.532788] ACPI: Power Button [PWRF]
[    1.072889] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[   12.737458] input: Logitech Optical USB Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/input/input3
[   12.737542] generic-usb 0003:046D:C016.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.0-1.4/input0
[   12.737557] usbcore: registered new interface driver usbhid
[   12.737559] usbhid: USB HID core driver
[   13.012220] IR NEC protocol handler initialized
[   13.013404] IR RC5(x) protocol handler initialized
[   13.014569] IR RC6 protocol handler initialized
[   13.015733] IR JVC protocol handler initialized
[   13.016898] IR Sony protocol handler initialized
[   13.018075] IR MCE Keyboard/mouse protocol handler initialized
[   13.019688] lirc_dev: IR Remote Control driver registered, major 249
[   13.020173] IR LIRC bridge handler initialized
[   13.357223] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input4

 Thanks for your help

---

### Post by Cas07 on 2013-06-24
I am seeing exactly the same issue on 13.04, it must be a driver issue, did you create a bug report for this?

---

### Post by bobrenard on 2013-06-28
> **Cas07 said:**
> I am seeing exactly the same issue on 13.04, it must be a driver issue, did you create a bug report for this?

No I do not , I bought an usb keyboard....

---

### Post by Bashing-om on 2013-06-28
I run a ps2 keyboard, have to set in bios for usb - enable "legacy" // no problems with any 'buntu installs up to and and inclusive of 13.04 .

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

