---
title: "Logitech DiNovo Media Desktop"
date: 2009-12-30
forum: Hardware
---

### Post by RA23 on 2009-12-30
Hi All,
I have just installed Ubuntu 9.10 on my HTPC and had a few issues with the DiNovo Media Desktop. It worked, but erratically. The keyboard would not work every so often and when that happened the mouse would travel, scroll and highlight, but I could not left or right click.
I googled but did not find any solutions, but here is what I did to get it working properly:

[LIST]
[*]Get rid of all bluetooth drivers (Bluez, etc) using Synaptic package manager - Note that even though the Logitech gear is bluetooth, its own dongle makes it look like a USB device to the OS.
[/LIST]

[LIST]
[*]In System > Preferences > Keyboards in the General tab, select the Logitech Dinovo Keyboard
[/LIST]

[LIST]
[*]Restart X and check if the devices are present. This is where other sources suggested to use /dev/input/eventX - this does not work (for me), because these devices get assigned new event numbers at startup.
[/LIST]
```
htpc@htpc:~$ ls /dev/input/by-id/
usb-Logitech_Logitech_BT_Mini-Receiver_000761A37727-event-kbd
usb-Logitech_Logitech_BT_Mini-Receiver_000761A37727-event-mouse
usb-Logitech_Logitech_BT_Mini-Receiver_000761A37727-mouse
```
[LIST]
[*]Edit xorg.conf to point to the right devices. Yes I know 9.10 is not supposed to "need" xorg.conf anymore, but my custom nvidia setup generated it anyway, so....  But seriously, if anyone knows how to do this properly instead, please let me know.
[/LIST]
```

Section "InputDevice"
    Identifier     "Logitech Media Desktop mouse"
    Driver         "evdev"
    Option         "Device" "/dev/input/by-id/usb-Logitech_Logitech_BT_Mini-Receiver_000761A37727-event-mouse"
    Option         "HWHEELRelativeAxisButtons" "7 8"
EndSection

Section "InputDevice"
    Identifier     "Logitech DiNovo Media Keyboard"
    Driver         "evdev"
    Option         "Device" "/dev/input/by-id/usb-Logitech_Logitech_BT_Mini-Receiver_000761A37727-event-kbd"
EndSection
```
This is it. Now my system works without keyboard or mouse glitches. I just wanted to post this somewhere in case anyone else has the same problem and also to suggest using the /dev/input/by-id/... approach, because that seems to make a lot of sense.
Note that I don't have any other bluetooth devices in this PC.

BTW: When you have problems with the keyboard - first check the batteries, it eats them.

Regards,
Edwin

---

