---
title: "keyboard issue"
date: 2009-04-27
forum: Hardware
---

### Post by abrazafi on 2009-04-27
Hi All,

I'm running kubuntu 8.10 and have multiple usernames on that machine.
Keyboard and mouse are logitech wireless sharing the same receptor
through USB. Somehow, the keyboard stopped working this morning. 
The mouse is still ok.

Again, only on my username, the keyboard doesn't work. And if I'm logging
in as different user, rather than mine, then the keyboard is working fine.
I tried to rebout/change to previous kernel versions, multiple times,
 without any success.

The Xorg.0.log file is fine: the keyboard and mouse are detected 

Any help will be apreciated.

Thanks,
Don.

-- Herewith the output from dmsg (only for keyboard and mouse):

[    5.896555] usbcore: registered new interface driver hiddev
[    5.897314] usbcore: registered new interface driver libusual
[    5.897953] input: Logitech Logitech USB Headset as /devices/pci0000:00/0000:00:1d.7/usb5/5-1/5-1.4/5-1.4:1.3/input/input1
[    5.908165] input,hidraw0: USB HID v1.00 Device [Logitech Logitech USB Headset] on usb-0000:00:1d.7-1.4
[    5.911814] Initializing USB Mass Storage driver...
[    5.922816] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/input/input2
[    5.923037] input,hidraw1: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.0-2
[    5.953095] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.1/input/input3
[    5.953463] input,hidraw2: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-2
[    5.953507] usbcore: registered new interface driver usbhid

---

### Post by abrazafi on 2009-04-28
Hi All,

After scratching my head, the issue is solved ...
I just deleted the .kde file from my top directory
and need to create/adjust my kde environment.

Because I suspect some conflict/errors from 
           ~/.xsession-errors  file

Cheers,
Don.

---

