---
title: "USB error message"
date: 2022-12-01
forum: Hardware
---

### Post by galluccib on 2022-12-01
Need some help trying to figure out what this error message means..

Had a few 3D Printer on Debian 11 with Octoprint and change system to intel 13th gen and Debian not doing well with the new CPU in the way it deals with the cores. So HP said Ubuntu 22.04 was supported so move over. When I have everything connected it seems fine. I start a print and anywhere from 10 to 20 mins the printer locks up and I see this error message in the log. Just to test I reconnected the printers using same USB cables to old Debian system and work with zero issues.

Error message is....
Dec  2 02:35:39 print-02 kernel: [ 3188.424132] usb 1-3: failed to send control message: -71
Dec  2 02:35:39 print-02 kernel: [ 3188.424604] usb 1-3: failed to send control message: -71
Dec  2 02:35:39 print-02 kernel: [ 3188.424805] usb 1-3: failed to receive control message: -71
Dec  2 02:35:39 print-02 kernel: [ 3188.424810] ch341-uart ttyUSB0: failed to read modem status: -71
Dec  2 02:35:39 print-02 kernel: [ 3188.427593] usb 1-3: failed to send control message: -71
Dec  2 02:35:39 print-02 kernel: [ 3188.427744] usb 1-3: failed to send control message: -71
Dec  2 02:35:39 print-02 kernel: [ 3188.427896] usb 1-3: failed to receive control message: -71
Dec  2 02:35:39 print-02 kernel: [ 3188.427897] ch341-uart ttyUSB0: failed to read modem status: -71
Dec  2 02:35:39 print-02 kernel: [ 3188.428778] usb 1-3: failed to send control message: -71
Dec  2 02:35:39 print-02 kernel: [ 3188.428927] usb 1-3: failed to send control message: -71
Dec  2 02:35:39 print-02 kernel: [ 3188.429082] usb 1-3: failed to receive control message: -71
Dec  2 02:35:39 print-02 kernel: [ 3188.429087] ch341-uart ttyUSB0: failed to read modem status: -71
Dec  2 02:35:39 print-02 kernel: [ 3188.429988] usb 1-3: failed to send control message: -71
Dec  2 02:35:39 print-02 kernel: [ 3188.430138] usb 1-3: failed to send control message: -71
Dec  2 02:35:39 print-02 kernel: [ 3188.430315] usb 1-3: failed to receive control message: -71

I googled -> failed to receive control message: -71 

And couldn't find anything about it.

---

