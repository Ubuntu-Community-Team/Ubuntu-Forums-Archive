---
title: "Touchpad not working on HP Spectre x360"
date: 2018-12-08
forum: Hardware
---

### Post by jabrilm on 2018-12-08
I've installed Ubuntu 18.04 on a new HP Spectre x360 convertible laptop. However, the touchpad does not work. It does work with a USB mouse though. 

This is the output of [FONT=courier new]xinput --list[/FONT] (with the USB mouse connected):

$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SIGMACHIP Usb Mouse                         id=10    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; HP Wide Vision FHD Camera: HP W             id=11    [slave  keyboard (3)]
    &#8627; HP Wide Vision FHD Camera: HP I             id=12    [slave  keyboard (3)]
    &#8627; Intel HID events                            id=13    [slave  keyboard (3)]
    &#8627; Intel HID 5 button array                    id=14    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=15    [slave  keyboard (3)]
    &#8627; HP WMI hotkeys                              id=16    [slave  keyboard (3)]
    &#8627; HP Wireless hotkeys                         id=17    [slave  keyboard (3)]

And this is the output of [FONT=courier new]lsusb[/FONT]:

Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 06cb:00bb Synaptics, Inc. 
Bus 001 Device 003: ID 04ca:7086 Lite-On Technology Corp. 
Bus 001 Device 005: ID 8087:0aaa Intel Corp. 
Bus 001 Device 006: ID 1c4f:0032 SiGma Micro 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

What can I do to get Ubuntu to recognize the touchpad?

---

### Post by jabrilm on 2018-12-09
I should add that the touchpad works fine in Windows 10 and also within Ubuntu 18.04 running in a VM within Windows 10.

---

