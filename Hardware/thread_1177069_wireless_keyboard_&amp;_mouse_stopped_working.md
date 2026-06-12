---
title: "wireless keyboard &amp; mouse stopped working"
date: 2009-06-03
forum: Hardware
---

### Post by duffrecords on 2009-06-03
I have a Micro Innovations KB990W USB wireless keyboard/mouse which previously worked with my Mythbuntu system.  Suddenly one night it stopped working, right after I finished watching a recorded program.  I thought the batteries were dead or the device might be defective so I tested it with my laptop and it works perfectly.  Both systems are running Jaunty Jackalope but the MythTV box obviously is a slightly modified distro.  It works automatically with my Debian Lenny box as well.  In fact, the MythTV box recognizes the USB transmitter when it's plugged in, but the keyboard and mouse don't work.  This is what I see in /var/log/messages:```
Jun  2 22:26:46 hollywood kernel: [  418.920022] usb 3-1: new low speed USB device using ohci_hcd and address 3
Jun  2 22:26:46 hollywood kernel: [  419.177516] usb 3-1: configuration #1 chosen from 1 choice
Jun  2 22:26:46 hollywood kernel: [  419.194457] input: MLK Wireless Keyboard and mouse as /devices/pci0000:00/0000:00:03.1/usb3/3-1/3-1:1.0/input/input8
Jun  2 22:26:46 hollywood kernel: [  419.195520] sunplus 0003:04FC:05D8.0003: input,hidraw0: USB HID v1.00 Keyboard [MLK Wireless Keyboard and mouse] on usb-0000:00:03.1-1/input0
Jun  2 22:26:46 hollywood kernel: [  419.228754] sunplus 0003:04FC:05D8.0004: fixing up Sunplus Wireless Desktop report descriptor
Jun  2 22:26:46 hollywood kernel: [  419.231165] input: MLK Wireless Keyboard and mouse as /devices/pci0000:00/0000:00:03.1/usb3/3-1/3-1:1.1/input/input9
Jun  2 22:26:47 hollywood kernel: [  419.329452] sunplus 0003:04FC:05D8.0004: input,hiddev96,hidraw1: USB HID v1.00 Mouse [MLK Wireless Keyboard and mouse] on usb-0000:00:03.1-1/input1
```My only guess is that my Xfce settings are wrong (the keyboard is set to "Generic 104-key PC" only because there is no "Micro Innovations" model in the list).

---

### Post by duffrecords on 2009-06-03
Also, here are the relevant sections of my xorg.conf:```
Section "InputDevice"
        Identifier     "Keyboard0"
        Driver         "keyboard"
EndSection

Section "InputDevice"
        Identifier     "Mouse0"
        Driver         "mouse"
        Option         "Protocol" "auto"
        Option         "Device" "/dev/psaux"
        Option         "Emulate3Buttons" "no"
        Option         "ZAxisMapping" "4 5"
        # generated from default
EndSection

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen         "Default Screen" 0 0
        InputDevice    "Keyboard0" "CoreKeyboard"
        InputDevice    "Mouse0" "CorePointer"
EndSection
```

---

### Post by duffrecords on 2009-06-04
Aha.  It needed to be set to "Generic 105-key (Intl)."  That's odd because choosing the right settings in Ubuntu made the keyboard work in BIOS again.  I would have thought hardware configuration at the BIOS level would be independent of the OS.

---

