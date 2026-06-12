---
title: "Finepoint Serial Stylus setup in Kharmic problems"
date: 2009-11-14
forum: Hardware
---

### Post by dlettrich on 2009-11-14
I recently installed Kharmic (fresh install from CD) on my Gateway CX2620.  This machine has a Finepoint pen running on serial port ttyS0.  I had this working in Jaunty by installing setserial and using two modified fpit drivers and editing the xorg.conf file.

I tried to follow the exact same steps in Kharmic, but since it doesn't have the xorg.conf file by default, I had to generate one from the console command and then put it in /etc/X11.  I am still getting no response from the pointer.

I did verify that the pen is communicating with the serial port by using cat, but the pointer never moves in X.  

Setserial was installed from the package manager, and I tried both the package version and the two modified fpit driver files pasted into usr/lib/xorg/modules/input ...neither method works.

So my /etc/serial.conf file contains:
/dev/ttyS0 autoconfig
/dev/ttyS0 uart 16550A port 0x3F8 irq 4 baud_base 38400

And /etc/X11/xorg.conf contains (extraneous stuff omitted):
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Tablet" "CorePointer"
EndSection
...
Section "InputDevice"
    Identifier  "Tablet"
    Driver      "fpit"
    Option      "Device" "/dev/ttyS0"
    Option        "AlwaysCore" "on"
    Option      "InvertY"
    Option      "MaximumXPosition" "12550"
    Option      "MaximumYPosition" "7650"
    Option      "MinimumXPosition" "400"
    Option      "MinumumYPosition" "400"
    Option      "SendCoreEvents"
EndSection

Any help would be greatly appreciated.  I really don't want to have to drop back to Jaunty to get the pen back.  It would be nice too, if I could do this through the fdi files, rather than relying on the old xorg.conf file method, since it seems to be a depreciated mechanism.  I just don't know how to identify the device, since it is serial and not really 'discoverable' like a USB one would be.

---

### Post by Favux on 2009-11-14
Hi dlettrich,

You'd think adding something like:
```
/dev/ttyS0 port 0x03F8 irq 4 autoconfig
```
to "/etc/serial.conf" followed by:
```
sudo /etc/init.d/setserial reload
```
would work.  Or maybe something like:
```
/dev/ttyS0 port 0x03F8 irq 4 baud_base 38400
```
But apparently the serial set up is non-standard.  TrevT93 got it working by following the [FujitsuStylus wiki]("https://help.ubuntu.com/community/FujitsuStylus").

Notice in "ServerLayout" the line may be:
```
InputDevice "Tablet"
```
Also you probably want to comment out (#):
```
InputDevice "Mouse0" "CorePointer"
InputDevice "Keyboard0" "CoreKeyboard"
```
And if you have them, the two sections that go with those lines.

---

### Post by fachex on 2010-04-30
I cannot make this driver work on Lucid..

---

