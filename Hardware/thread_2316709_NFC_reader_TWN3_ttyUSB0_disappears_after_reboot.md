---
title: "NFC reader TWN3 ttyUSB0 disappears after reboot"
date: 2016-03-10
forum: Hardware
---

### Post by opr on 2016-03-10
Hello,

So, I have this problem for around a week now, and it is driving me crazy.

I'm on ubuntu 14.04 lts x64.
I have multiple usb-serial converters, and an NFC_TWN3 rfid device.
User already added to dialout group.

So, the situation is:
If I plug in the nfc only after reboot, there is no ttyUSBx.
After _sudo modprobe usbserial vendor=0x09d8 product=0x0320_, I receive the message:
"usbserial_generic 3-5:1.0: Generic device with no bulk out, not allowed"

dmesg | tail:

[  813.949331] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[ 1072.941146] usbcore: registered new interface driver usbserial
[ 1072.941152] usbcore: registered new interface driver usbserial_generic
[ 1072.941156] usbserial: USB Serial support registered for generic
[ 1072.941165] usbserial_generic 3-5:1.0: Generic device with no bulk out, not allowed.
[ 1072.941220] usbserial_generic: probe of 3-5:1.0 failed with error -5
[ 1072.941222] usbserial_generic 3-5:1.1: The "generic" usb-serial driver is only for testing and one-off prototypes.
[ 1072.941223] usbserial_generic 3-5:1.1: Tell [EMAIL="linux-usb@vger.kernel.org"]linux-usb@vger.kernel.org[/EMAIL] to add your device to a proper driver.
[ 1072.941224] usbserial_generic 3-5:1.1: generic converter detected
[ 1072.941323] usb 3-5: generic converter now attached to ttyUSB0



ttyUSB0 appears, but only if there are no other usbserial devices installed! (If there is another one, nothing happens when I type this)
If I remove & replug the device, dmesg | tail messages:
remove:

[ 1251.047188] usb 3-5: USB disconnect, device number 12
[ 1251.047534] generic ttyUSB0: generic converter now disconnected from ttyUSB0
[ 1251.047569] usbserial_generic 3-5:1.1: device disconnected

replug:
[ 1282.362554] usb 3-5: new full-speed USB device number 13 using xhci_hcd
[ 1282.383889] usb 3-5: New USB device found, idVendor=09d8, idProduct=0320
[ 1282.383898] usb 3-5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 1282.383903] usb 3-5: Product: RFID Device (COM)
[ 1282.383907] usb 3-5: Manufacturer: OEM
[ 1282.385582] cdc_acm 3-5:1.0: Zero length descriptor references
[ 1282.385689] cdc_acm: probe of 3-5:1.0 failed with error -22
[ 1282.385703] usbserial_generic 3-5:1.0: Generic device with no bulk out, not allowed.
[ 1282.385803] usbserial_generic: probe of 3-5:1.0 failed with error -5
[ 1282.385887] usbserial_generic 3-5:1.1: The "generic" usb-serial driver is only for testing and one-off prototypes.
[ 1282.385891] usbserial_generic 3-5:1.1: Tell [EMAIL="linux-usb@vger.kernel.org"]linux-usb@vger.kernel.org[/EMAIL] to add your device to a proper driver.
[ 1282.385894] usbserial_generic 3-5:1.1: generic converter detected
[ 1282.386054] usb 3-5: generic converter now attached to ttyUSB0

And, after replugged, I get the following message in terminal:
cdc_acm 3-5:1.0: Zero length descriptor references
usbserial_generic 3-5:1.0: Generic device with no bulk out, not allowed.

But, after restart, NFC_TWN3 disappears, even if I add 
usbserial vendor=0x09d8 product=0x0320
to /etc/modules.


My questions are:
How can I make NFC_TWN3 appear on ttyUSBx after every boot, without any manual action



How can I permanently attach usb3-5 to ttyUSBx (I don't care if it's not always the same number after ttyUSB, I'll handle that with an udev rule.)


Thanks in advance for any help!

---

