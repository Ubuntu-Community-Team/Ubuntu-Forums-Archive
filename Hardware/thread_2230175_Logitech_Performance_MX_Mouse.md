---
title: "Logitech Performance MX Mouse"
date: 2014-06-17
forum: Hardware
---

### Post by jtliiiis on 2014-06-17
I have a brand new Logitch Performance MX mouse and a K800 keyboard. They came as a desktop combo with a unifying receiver. The keyboard works fine in every operating system I have tried but the mouse only works in Windows. I am running a dual boot system with Windows 7 64-bit and Linux. Again the mouse works fine in Windows but it does not work in Ubuntu 14.04 LTS, Minut 16, or Mint 17. Mint 17 and Ubuntu 14.04 LTS have been fresh installs. I have a cheap Dell USB mouse attached as well and it works in all systems which I would expect. Any ideas how to get this thing working or do I just quit using Linux?

Thanks

John

---

### Post by whatthefunk on 2014-06-17
The problem is most likely with the unifying receiver.  Id try installing the program Solaar.
[http://www.omgubuntu.co.uk/2013/12/logitech-unifying-receiver-linux-solaar](http://www.omgubuntu.co.uk/2013/12/logitech-unifying-receiver-linux-solaar)
That worked for me (although not with that specific mouse).

---

### Post by jtliiiis on 2014-06-19
Thanks for the suggestion. I did a fresh install of Mint 17, installed Solaar and it detected the keyboard but still not the mouse. The Performance MX mouse is listed as supported though in the Solaar documentation. I know this mouse works because it works fine in Windows on the same system.

---

### Post by whatthefunk on 2014-06-19
Okay, well lets see if your mouse is at least detected by the system.  In a terminal, run "xinput list" and post the output here.

---

### Post by kirenpillay1 on 2014-08-18
Hi

I think I'm having the same problem. When plugged in, I cannot click on any clicakble items on the screen. The touchpad doesn't work either. If I unplug the receiver, then everything works fine. I use an old external mouse and everything is fine.

Please see my logs below:

Before:

kiren@Pillay-on-Steroids:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                          id=11    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; HP HD Webcam [Fixed]                        id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]
    &#8627; HP WMI hotkeys                              id=13    [slave  keyboard (3)]
    &#8627; HP Wireless hotkeys                         id=14    [slave  keyboard (3)]

After:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                          id=11    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; HP HD Webcam [Fixed]                        id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]
    &#8627; HP WMI hotkeys                              id=13    [slave  keyboard (3)]
    &#8627; HP Wireless hotkeys                         id=14    [slave  keyboard (3)]


This is the output of my dmesg. Interestingly the device number keeps increasing even though I'm unplugging and plugging it into the same USB port. 

[  262.759152] usb 3-4: new full-speed USB device number 2 using xhci_hcd
[  262.778090] usb 3-4: New USB device found, idVendor=046d, idProduct=c52b
[  262.778097] usb 3-4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  262.778101] usb 3-4: Product: USB Receiver
[  262.778104] usb 3-4: Manufacturer: Logitech
[  262.796244] hidraw: raw HID events driver (C) Jiri Kosina
[  262.804155] usbcore: registered new interface driver usbhid
[  262.804160] usbhid: USB HID core driver
[  262.809052] logitech-djreceiver 0003:046D:C52B.0003: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:14.0-4/input2
[  266.086665] input: Logitech Unifying Device. Wireless PID:101a as /devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4:1.2/0003:046D:C52B.0003/input/input23
[  266.087214] logitech-djdevice 0003:046D:C52B.0004: input,hidraw1: USB HID v1.11 Mouse [Logitech Unifying Device. Wireless PID:101a] on usb-0000:00:14.0-4:1
[ 1169.945021] usb 3-4: USB disconnect, device number 2
[ 1656.131820] type=1400 audit(1408350085.908:77): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=4235 comm="apparmor_parser"
[ 1656.131827] type=1400 audit(1408350085.908:78): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=4235 comm="apparmor_parser"
[ 1656.132206] type=1400 audit(1408350085.908:79): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=4235 comm="apparmor_parser"
[ 6505.123953] usb 3-4: new full-speed USB device number 3 using xhci_hcd
[ 6505.142822] usb 3-4: New USB device found, idVendor=046d, idProduct=c52b
[ 6505.142830] usb 3-4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 6505.142834] usb 3-4: Product: USB Receiver
[ 6505.142837] usb 3-4: Manufacturer: Logitech
[ 6505.148312] logitech-djreceiver 0003:046D:C52B.0007: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:14.0-4/input2
[ 6577.304836] input: Logitech Unifying Device. Wireless PID:101a as /devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4:1.2/0003:046D:C52B.0007/input/input24
[ 6577.305405] logitech-djdevice 0003:046D:C52B.0008: input,hidraw1: USB HID v1.11 Mouse [Logitech Unifying Device. Wireless PID:101a] on usb-0000:00:14.0-4:1
[ 7199.558572] usb 3-4: USB disconnect, device number 3
[ 7263.750932] usb 3-3: new full-speed USB device number 4 using xhci_hcd
[ 7263.769638] usb 3-3: New USB device found, idVendor=046d, idProduct=c52b
[ 7263.769646] usb 3-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 7263.769649] usb 3-3: Product: USB Receiver
[ 7263.769652] usb 3-3: Manufacturer: Logitech
[ 7263.775106] logitech-djreceiver 0003:046D:C52B.000B: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:14.0-3/input2
[ 7280.339275] usb 3-3: USB disconnect, device number 4
[ 7291.110218] usb 3-3: new full-speed USB device number 5 using xhci_hcd
[ 7291.129095] usb 3-3: New USB device found, idVendor=046d, idProduct=c52b
[ 7291.129102] usb 3-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 7291.129106] usb 3-3: Product: USB Receiver
[ 7291.129109] usb 3-3: Manufacturer: Logitech
[ 7291.134846] logitech-djreceiver 0003:046D:C52B.000E: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:14.0-3/input2
[ 7376.905798] usb 3-3: USB disconnect, device number 5
[ 7390.854499] usb 3-3: new full-speed USB device number 6 using xhci_hcd
[ 7390.873353] usb 3-3: New USB device found, idVendor=046d, idProduct=c52b
[ 7390.873361] usb 3-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 7390.873365] usb 3-3: Product: USB Receiver
[ 7390.873368] usb 3-3: Manufacturer: Logitech
[ 7390.879110] logitech-djreceiver 0003:046D:C52B.0011: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:14.0-3/input2
[ 7621.898375] usb 3-3: USB disconnect, device number 6




If I tail /var/log/Xorg.0.log. I notice only one unplug is detected. I don't get the subsequent plug/unplugs.

[   266.116] (**) Logitech Unifying Device. Wireless PID:101a: Applying InputClass "evdev pointer catchall"
[   266.116] (II) Using input driver 'evdev' for 'Logitech Unifying Device. Wireless PID:101a'
[   266.116] (**) Logitech Unifying Device. Wireless PID:101a: always reports core events
[   266.116] (**) evdev: Logitech Unifying Device. Wireless PID:101a: Device: "/dev/input/event17"
[   266.124] (--) evdev: Logitech Unifying Device. Wireless PID:101a: Vendor 0x46d Product 0xc52b
[   266.124] (--) evdev: Logitech Unifying Device. Wireless PID:101a: Found 20 mouse buttons
[   266.124] (--) evdev: Logitech Unifying Device. Wireless PID:101a: Found scroll wheel(s)
[   266.124] (--) evdev: Logitech Unifying Device. Wireless PID:101a: Found relative axes
[   266.124] (--) evdev: Logitech Unifying Device. Wireless PID:101a: Found x and y relative axes
[   266.124] (II) evdev: Logitech Unifying Device. Wireless PID:101a: Configuring as mouse
[   266.124] (II) evdev: Logitech Unifying Device. Wireless PID:101a: Adding scrollwheel support
[   266.124] (**) evdev: Logitech Unifying Device. Wireless PID:101a: YAxisMapping: buttons 4 and 5
[   266.124] (**) evdev: Logitech Unifying Device. Wireless PID:101a: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   266.124] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4:1.2/0003:046D:C52B.0003/input/input23/event17"
[   266.124] (II) XINPUT: Adding extended input device "Logitech Unifying Device. Wireless PID:101a" (type: MOUSE, id 15)
[   266.124] (II) evdev: Logitech Unifying Device. Wireless PID:101a: initialized for relative axes.
[   266.125] (**) Logitech Unifying Device. Wireless PID:101a: (accel) keeping acceleration scheme 1
[   266.125] (**) Logitech Unifying Device. Wireless PID:101a: (accel) acceleration profile 0
[   266.125] (**) Logitech Unifying Device. Wireless PID:101a: (accel) acceleration factor: 2.000
[   266.125] (**) Logitech Unifying Device. Wireless PID:101a: (accel) acceleration threshold: 4
[  1170.269] (II) config/udev: removing device Logitech Unifying Device. Wireless PID:101a
[  1170.281] (II) evdev: Logitech Unifying Device. Wireless PID:101a: Close
[  1170.281] (II) UnloadModule: "evdev"
[  6579.339] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:101a (/dev/input/mouse2)
[  6579.339] (II) No input driver specified, ignoring this device.
[  6579.339] (II) This device may have been added with another device file.
[  6579.339] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:101a (/dev/input/event17)
[  6579.339] (**) Logitech Unifying Device. Wireless PID:101a: Applying InputClass "evdev pointer catchall"
[  6579.340] (II) Using input driver 'evdev' for 'Logitech Unifying Device. Wireless PID:101a'
[  6579.340] (**) Logitech Unifying Device. Wireless PID:101a: always reports core events
[  6579.340] (**) evdev: Logitech Unifying Device. Wireless PID:101a: Device: "/dev/input/event17"
[  6579.356] (--) evdev: Logitech Unifying Device. Wireless PID:101a: Vendor 0x46d Product 0xc52b
[  6579.356] (--) evdev: Logitech Unifying Device. Wireless PID:101a: Found 20 mouse buttons
[  6579.356] (--) evdev: Logitech Unifying Device. Wireless PID:101a: Found scroll wheel(s)
[  6579.356] (--) evdev: Logitech Unifying Device. Wireless PID:101a: Found relative axes
[  6579.356] (--) evdev: Logitech Unifying Device. Wireless PID:101a: Found x and y relative axes
[  6579.356] (II) evdev: Logitech Unifying Device. Wireless PID:101a: Configuring as mouse
[  6579.356] (II) evdev: Logitech Unifying Device. Wireless PID:101a: Adding scrollwheel support
[  6579.356] (**) evdev: Logitech Unifying Device. Wireless PID:101a: YAxisMapping: buttons 4 and 5
[  6579.356] (**) evdev: Logitech Unifying Device. Wireless PID:101a: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  6579.356] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4:1.2/0003:046D:C52B.0007/input/input24/event17"
[  6579.356] (II) XINPUT: Adding extended input device "Logitech Unifying Device. Wireless PID:101a" (type: MOUSE, id 15)
[  6579.357] (II) evdev: Logitech Unifying Device. Wireless PID:101a: initialized for relative axes.
[  6579.357] (**) Logitech Unifying Device. Wireless PID:101a: (accel) keeping acceleration scheme 1
[  6579.357] (**) Logitech Unifying Device. Wireless PID:101a: (accel) acceleration profile 0
[  6579.357] (**) Logitech Unifying Device. Wireless PID:101a: (accel) acceleration factor: 2.000
[  6579.357] (**) Logitech Unifying Device. Wireless PID:101a: (accel) acceleration threshold: 4
[  7201.792] (II) config/udev: removing device Logitech Unifying Device. Wireless PID:101a
[  7201.804] (II) evdev: Logitech Unifying Device. Wireless PID:101a: Close
[  7201.804] (II) UnloadModule: "evdev"

---

### Post by whatthefunk on 2014-08-18
Whats the model number of your mouse and keyboard?

---

