---
title: "usb sound card not detected with aplay but is there with lsusb"
date: 2007-10-18
forum: Hardware &amp; Laptops
---

### Post by mjkelly on 2007-10-18
Ive been searching all afternoon for a fix to this.

Heres my aplay -l:
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

And onboard audio works fine.

Heres my lsusb:
Bus 005 Device 003: ID 0bda:8187 Realtek Semiconductor Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0c45:1677 Microdia 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c51b Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  

And Microdia is my external usb sound card device.

lsmod shows snd-usb-audio as listed.

Why wont this card appear on my aplay list? Im open to all kinds of suggestions at this point. Im using 7.04 atm until 7.10 finishes downloading.

EDIT: ok heres a little bit from dmesg:

[ 6513.684000] usb 1-1: USB disconnect, address 3
[ 6517.644000] usb 1-2: new full speed USB device using uhci_hcd and address 4
[ 6517.860000] usb 1-2: configuration #1 chosen from 1 choice
[ 6517.864000] cannot find the slot for index 0 (range 0-0)
[ 6517.864000] cannot create card instance 0
[ 6517.864000] snd-usb-audio: probe of 1-2:1.0 failed with error -5
[ 6517.864000] usb 1-2: device_add(1-2:1.0) --> -5
[ 6517.868000] input: USB Audio as /class/input/input10
[ 6517.868000] input: USB HID v1.00 Device [USB Audio] on usb-0000:00:1d.0-2

[   17.720000] usbcore: registered new interface driver rtl8187
[   17.720000] cannot find the slot for index 0 (range 0-0)
[   17.720000] cannot create card instance 0
[   17.720000] snd-usb-audio: probe of 1-1:1.0 failed with error -5
[   17.720000] usbcore: registered new interface driver snd-usb-audio

Not sure what to make of that. And btw ive seen something similar to this in the bug tracker.

---

### Post by Face1 on 2007-11-26
I'm having the exact same issue, with an external Creative card.  Can anyone lend any advice, please?

---

