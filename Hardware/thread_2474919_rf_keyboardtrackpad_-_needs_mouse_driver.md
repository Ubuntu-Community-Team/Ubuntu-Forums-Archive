---
title: "rf keyboard/trackpad - needs mouse driver"
date: 2022-05-11
forum: Hardware
---

### Post by kmand on 2022-05-11
I have  a SIIG keboard/trackpad combo that operates over rf with a usb rf receiver. This is of course meant for windows. Surprisingly to me the receiver is recognized and the keyboard works. On the other hand as far as the trackpad, what Linux sees from syslog and lshw follows.

Any chance of getting the "mouse" to work?

May 11 12:40:36 orac kernel: [1031465.504911] usb 3-7.1.2: new low-speed USB device number 97 using xhci_hcd
May 11 12:40:36 orac kernel: [1031465.670106] usb 3-7.1.2: New USB device found, idVendor=0040, idProduct=073d, bcdDevice= 1.00
May 11 12:40:36 orac kernel: [1031465.670110] usb 3-7.1.2: New USB device strings: Mfr=0, Product=2, SerialNumber=0
May 11 12:40:36 orac kernel: [1031465.670112] usb 3-7.1.2: Product: 2.4 GHz RF Receiver
May 11 12:40:36 orac kernel: [1031465.686738] input: 2.4 GHz RF Receiver as /devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7.1/3-7.1.2/3-7.1.2:1.0/0003:0040:073D.0008/input/input31
May 11 12:40:36 orac kernel: [1031465.745229] hid-generic 0003:0040:073D.0008: input,hidraw4: USB HID v1.10 Keyboard [2.4 GHz RF Receiver] on usb-0000:00:14.0-7.1.2/input0
May 11 12:40:36 orac kernel: [1031465.761010] input: 2.4 GHz RF Receiver Mouse as /devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7.1/3-7.1.2/3-7.1.2:1.1/0003:0040:073D.0009/input/input32
May 11 12:40:36 orac kernel: [1031465.761195] input: 2.4 GHz RF Receiver Consumer Control as /devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7.1/3-7.1.2/3-7.1.2:1.1/0003:0040:073D.0009/input/input33
May 11 12:40:36 orac kernel: [1031465.821143] input: 2.4 GHz RF Receiver System Control as /devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7.1/3-7.1.2/3-7.1.2:1.1/0003:0040:073D.0009/input/input34
May 11 12:40:36 orac kernel: [1031465.821253] input: 2.4 GHz RF Receiver as /devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7.1/3-7.1.2/3-7.1.2:1.1/0003:0040:073D.0009/input/input35
May 11 12:40:36 orac kernel: [1031465.821364] hid-generic 0003:0040:073D.0009: input,hiddev2,hidraw5: USB HID v1.10 Mouse [2.4 GHz RF Receiver] on usb-0000:00:14.0-7.1.2/input1
May 11 12:40:36 orac mtp-probe: checking bus 3, device 97: "/sys/devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7.1/3-7.1.2"
May 11 12:40:36 orac mtp-probe: bus: 3, device: 97 was not an MTP device
May 11 12:40:36 orac /usr/libexec/gdm-x-session[699549]: (II) config/udev: Adding input device 2.4 GHz RF Receiver Mouse (/dev/input/mouse1)
May 11 12:40:36 orac /usr/libexec/gdm-x-session[699549]: (II) No input driver specified, ignoring this device.
May 11 12:40:36 orac /usr/libexec/gdm-x-session[699549]: (II) This device may have been added with another device file.
May 11 12:40:36 orac /usr/libexec/gdm-x-session[699549]: (II) config/udev: Adding input device 2.4 GHz RF Receiver (/dev/input/event23)
May 11 12:40:36 orac /usr/libexec/gdm-x-session[699549]: (II) No input driver specified, ignoring this device.
May 11 12:40:36 orac /usr/libexec/gdm-x-session[699549]: (II) This device may have been added with another device file.
May 11 12:40:36 orac /usr/libexec/gdm-x-session[699549]: (II) config/udev: Adding input device 2.4 GHz RF Receiver System Control (/dev/input/event22)
May 11 12:40:36 orac /usr/libexec/gdm-x-session[699549]: (**) 2.4 GHz RF Receiver System Control: Applying InputClass "libinput keyboard catchall"
May 11 12:40:36 orac /usr/libexec/gdm-x-session[699549]: (II) Using input driver 'libinput' for '2.4 GHz RF Receiver System Control'
May 11 12:40:36 orac /usr/libexec/gdm-x-session[699549]: (II) systemd-logind: got fd for /dev/input/event22 13:86 fd 70 paused 0
May 11 12:40:36 orac /usr/libexec/gdm-x-session[699549]: (**) 2.4 GHz RF Receiver System Control: always reports core events
May 11 12:40:36 orac /usr/libexec/gdm-x-session[699549]: (**) Option "Device" "/dev/input/event22"
May 11 12:40:36 orac mtp-probe: checking bus 3, device 97: "/sys/devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7.1/3-7.1.2"
May 11 12:40:36 orac mtp-probe: bus: 3, device: 97 was not an MTP device
May 11 12:40:36 orac /usr/libexec/gdm-x-session[699549]: (II) event22 - 2.4 GHz RF Receiver System Control: is tagged by udev as: Keyboard
May 11 12:40:36 orac /usr/libexec/gdm-x-session[699549]: (II) event22 - 2.4 GHz RF Receiver System Control: device is a keyboard
May 11 12:40:36 orac /usr/libexec/gdm-x-session[699549]: (II) event22 - 2.4 GHz RF Receiver System Control: device removed
May 11 12:40:36 orac /usr/libexec/gdm-x-session[699549]: (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7.1/3-7.1.2/3-7.1.2:1.1/0003:0040:073D.0009/input/input34/event22"
May 11 12:40:36 orac /usr/libexec/gdm-x-session[699549]: (II) XINPUT: Adding extended input device "2.4 GHz RF Receiver System Control" (type: KEYBOARD, id 14)
May 11 12:40:36 orac /usr/libexec/gdm-x-session[699549]: (**) Option "xkb_model" "pc105"
May 11 12:40:36 orac /usr/libexec/gdm-x-session[699549]: (**) Option "xkb_layout" "us"
May 11 12:40:36 orac /usr/libexec/gdm-x-session[699549]: (WW) Option "xkb_variant" requires a string value
May 11 12:40:36 orac /usr/libexec/gdm-x-session[699549]: (WW) Option "xkb_options" requires a string value
May 11 12:40:36 orac /usr/libexec/gdm-x-session[699549]: (II) event22 - 2.4 GHz RF Receiver System Control: is tagged by udev as: Keyboard
May 11 12:40:36 orac /usr/libexec/gdm-x-session[699549]: (II) event22 - 2.4 GHz RF Receiver System Control: device is a keyboard
May 11 12:40:36 orac /usr/libexec/gdm-x-session[699549]: (II) config/udev: Adding input device 2.4 GHz RF Receiver Consumer Control (/dev/input/event21)
May 11 12:40:36 orac /usr/libexec/gdm-x-session[699549]: (**) 2.4 GHz RF Receiver Consumer Control: Applying InputClass "libinput keyboard catchall"
May 11 12:40:36 orac /usr/libexec/gdm-x-session[699549]: (II) Using input driver 'libinput' for '2.4 GHz RF Receiver Consumer Control'
May 11 12:40:36 orac /usr/libexec/gdm-x-session[699549]: (II) systemd-logind: got fd for /dev/input/event21 13:85 fd 72 paused 0
May 11 12:40:36 orac /usr/libexec/gdm-x-session[699549]: (**) 2.4 GHz RF Receiver Consumer Control: always reports core events
May 11 12:40:36 orac /usr/libexec/gdm-x-session[699549]: (**) Option "Device" "/dev/input/event21"
May 11 12:40:36 orac /usr/libexec/gdm-x-session[699549]: (II) event21 - 2.4 GHz RF Receiver Consumer Control: is tagged by udev as: Keyboard
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (II) event21 - 2.4 GHz RF Receiver Consumer Control: device is a keyboard
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (II) event21 - 2.4 GHz RF Receiver Consumer Control: device removed
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (II) libinput: 2.4 GHz RF Receiver Consumer Control: needs a virtual subdevice
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7.1/3-7.1.2/3-7.1.2:1.1/0003:0040:073D.0009/input/input33/event21"
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (II) XINPUT: Adding extended input device "2.4 GHz RF Receiver Consumer Control" (type: MOUSE, id 15)
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (**) Option "AccelerationScheme" "none"
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (**) 2.4 GHz RF Receiver Consumer Control: (accel) selected scheme none/0
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (**) 2.4 GHz RF Receiver Consumer Control: (accel) acceleration factor: 2.000
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (**) 2.4 GHz RF Receiver Consumer Control: (accel) acceleration threshold: 4
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (II) event21 - 2.4 GHz RF Receiver Consumer Control: is tagged by udev as: Keyboard
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (II) event21 - 2.4 GHz RF Receiver Consumer Control: device is a keyboard
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (**) 2.4 GHz RF Receiver Consumer Control: Applying InputClass "libinput keyboard catchall"
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (II) Using input driver 'libinput' for '2.4 GHz RF Receiver Consumer Control'
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (II) systemd-logind: returning pre-existing fd for /dev/input/event21 13:85
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (**) 2.4 GHz RF Receiver Consumer Control: always reports core events
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (**) Option "Device" "/dev/input/event21"
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (II) libinput: 2.4 GHz RF Receiver Consumer Control: is a virtual subdevice
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7.1/3-7.1.2/3-7.1.2:1.1/0003:0040:073D.0009/input/input33/event21"
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (II) XINPUT: Adding extended input device "2.4 GHz RF Receiver Consumer Control" (type: KEYBOARD, id 16)
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (**) Option "xkb_model" "pc105"
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (**) Option "xkb_layout" "us"
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (WW) Option "xkb_variant" requires a string value
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (WW) Option "xkb_options" requires a string value
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (II) config/udev: Adding input device 2.4 GHz RF Receiver (/dev/input/event19)
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (**) 2.4 GHz RF Receiver: Applying InputClass "libinput keyboard catchall"
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (II) Using input driver 'libinput' for '2.4 GHz RF Receiver'
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (II) systemd-logind: got fd for /dev/input/event19 13:83 fd 85 paused 0
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (**) 2.4 GHz RF Receiver: always reports core events
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (**) Option "Device" "/dev/input/event19"
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (II) event19 - 2.4 GHz RF Receiver: is tagged by udev as: Keyboard
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (II) event19 - 2.4 GHz RF Receiver: device is a keyboard
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (II) event19 - 2.4 GHz RF Receiver: device removed
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7.1/3-7.1.2/3-7.1.2:1.0/0003:0040:073D.0008/input/input31/event19"
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (II) XINPUT: Adding extended input device "2.4 GHz RF Receiver" (type: KEYBOARD, id 17)
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (**) Option "xkb_model" "pc105"
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (**) Option "xkb_layout" "us"
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (WW) Option "xkb_variant" requires a string value
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (WW) Option "xkb_options" requires a string value
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (II) event19 - 2.4 GHz RF Receiver: is tagged by udev as: Keyboard
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (II) event19 - 2.4 GHz RF Receiver: device is a keyboard
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (II) config/udev: Adding input device 2.4 GHz RF Receiver Mouse (/dev/input/event20)
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (**) 2.4 GHz RF Receiver Mouse: Applying InputClass "libinput pointer catchall"
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (II) Using input driver 'libinput' for '2.4 GHz RF Receiver Mouse'
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (II) systemd-logind: got fd for /dev/input/event20 13:84 fd 88 paused 0
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (**) 2.4 GHz RF Receiver Mouse: always reports core events
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (**) Option "Device" "/dev/input/event20"
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (II) event20 - 2.4 GHz RF Receiver Mouse: is tagged by udev as: Mouse
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (II) event20 - 2.4 GHz RF Receiver Mouse: device is a pointer
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (II) event20 - 2.4 GHz RF Receiver Mouse: device removed
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7.1/3-7.1.2/3-7.1.2:1.1/0003:0040:073D.0009/input/input32/event20"
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (II) XINPUT: Adding extended input device "2.4 GHz RF Receiver Mouse" (type: MOUSE, id 18)
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (**) Option "AccelerationScheme" "none"
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (**) 2.4 GHz RF Receiver Mouse: (accel) selected scheme none/0
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (**) 2.4 GHz RF Receiver Mouse: (accel) acceleration factor: 2.000
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (**) 2.4 GHz RF Receiver Mouse: (accel) acceleration threshold: 4
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (II) event20 - 2.4 GHz RF Receiver Mouse: is tagged by udev as: Mouse
May 11 12:40:37 orac /usr/libexec/gdm-x-session[699549]: (II) event20 - 2.4 GHz RF Receiver Mouse: device is a pointer



-usb:1
                         description: Keyboard
                         product: 2.4 GHz RF Receiver
                         physical id: 2
                         bus info: usb@3:7.1.2
                         logical name: input31
                         logical name: /dev/input/event19
                         logical name: input31::capslock
                         logical name: input31::compose
                         logical name: input31::kana
                         logical name: input31::numlock
                         logical name: input31::scrolllock
                         logical name: input32
                         logical name: /dev/input/event20
                         logical name: /dev/input/mouse1
                         logical name: input33
                         logical name: /dev/input/event21
                         logical name: input34
                         logical name: /dev/input/event22
                         logical name: input35

---

