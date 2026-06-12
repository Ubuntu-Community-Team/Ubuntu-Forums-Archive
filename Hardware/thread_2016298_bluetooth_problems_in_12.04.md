---
title: "bluetooth problems in 12.04"
date: 2012-07-04
forum: Hardware
---

### Post by 4thfloorstudios on 2012-07-04
Hi,
I have a problem with my Toshiba Tecra-S11 and Bluetooth.

In the syslog I see that the bluetooth daemon tries to enable bluetooth all the time and I have Bluetooth turned off at startup so I wonder how I can tell the daemon to stop that :)

Here is an excerpt of the syslog (the bluetooth messages are repeated on and on):

```
Jul  4 14:00:56 oliver-TECRA bluetoothd[1080]: HCI dev 0 registered
Jul  4 14:00:56 oliver-TECRA bluetoothd[1080]: Listening for HCI events on hci0
Jul  4 14:00:56 oliver-TECRA bluetoothd[11648]: Can't init device hci0: Operation not possible due to RF-kill (132)
Jul  4 14:00:59 oliver-TECRA kernel: [  804.111700] toshiba_bluetooth: Re-enabling Toshiba Bluetooth
Jul  4 14:00:59 oliver-TECRA bluetoothd[1080]: HCI dev 0 unregistered
Jul  4 14:00:59 oliver-TECRA bluetoothd[1080]: Stopping hci0 event socket
Jul  4 14:00:59 oliver-TECRA kernel: [  804.297096] usb 1-1.6: USB disconnect, device number 106
Jul  4 14:00:59 oliver-TECRA kernel: [  804.623412] usb 1-1.6: new full-speed USB device number 107 using ehci_hcd
Jul  4 14:00:59 oliver-TECRA kernel: [  804.695237] usb 1-1.6: device descriptor read/64, error -32
Jul  4 14:01:01 oliver-TECRA bluetoothd[1080]: HCI dev 0 registered
Jul  4 14:01:01 oliver-TECRA bluetoothd[1080]: Listening for HCI events on hci0
Jul  4 14:01:01 oliver-TECRA bluetoothd[11678]: Can't init device hci0: Operation not possible due to RF-kill (132)
Jul  4 14:01:04 oliver-TECRA kernel: [  809.091927] toshiba_bluetooth: Re-enabling Toshiba Bluetooth
Jul  4 14:01:04 oliver-TECRA bluetoothd[1080]: HCI dev 0 unregistered
Jul  4 14:01:04 oliver-TECRA bluetoothd[1080]: Stopping hci0 event socket
Jul  4 14:01:04 oliver-TECRA kernel: [  809.148432] usb 1-1.6: USB disconnect, device number 107
Jul  4 14:01:04 oliver-TECRA kernel: [  809.602927] usb 1-1.6: new full-speed USB device 
number 108 using ehci_hcd
Jul  4 14:01:04 oliver-TECRA kernel: [  809.674751] usb 1-1.6: device descriptor read/64, error -32
Jul  4 14:01:05 oliver-TECRA kernel: [  809.850269] usb 1-1.6: device descriptor read/64, error -32
Jul  4 14:01:05 oliver-TECRA kernel: [  810.025819] usb 1-1.6: new full-speed USB device number 109 using ehci_hcd
Jul  4 14:01:06 oliver-TECRA bluetoothd[1080]: HCI dev 0 registered
Ju
```Can anyone help me out? I recently had a kernel panic (blinking caps lock) at startup and wonder if that is related to the bluetooth problem.

Thanks!!

Oliver

---

### Post by arturiu on 2012-07-13
Hi,

I have a Toshiba Tecra M11 and also experience these error messages in my system.
Using Ubuntu 12.04 64bit with current updates.

Any idea of what it is ?

FYI, I have Jupiter 0.1.2 running. Turning bluetooth off is often done via this utility.

Tks,

/arturiu

---

