---
title: "Mouse not detected"
date: 2005-03-25
forum: Hardware &amp; Laptops
---

### Post by marceloide on 2005-03-25
Hi everyone, I'm new in Ubuntu, I just installed it today and it didn't detect my mouse. Is is anything I can do? I don't even know how to use the keyboard in Ubuntu (I mean hotkeys, etc)

anyone help me out, please!


bye

---

### Post by msmith on 2005-03-25
Hi,

Assuming it recognized your keyboard correctly, you'll need to escape to a console with CTRL+ALT+F1. (You can get back to your X session later with ALT+F7). Login as yourself to get a shell prompt. If it's a usb mouse, type:

$ lsmod | egrep hid

If it's a usb mouse and you don't see output that looks something like this:

usbhid                 29376  0
usbcore               107384  3 usbhid,uhci_hcd

, you'll need to load the usbhid (human interface device) driver with modprobe.

If it isn't a usb mouse, you'll need the spcific driver for it.

Then you'll need to edit /etc/X11/xorg.conf or /etc/X11/XFree86.conf 

The relevant section in mine looks like this:

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

There may be other things that need to be done too, but this should get you started.

---

### Post by marceloide on 2005-05-20
Hey man, thanx a lot. Im gonna try it

Sorry for the delay (2 months) hehe... some problems around, you know.

Thanx again.

---

### Post by marceloide on 2005-05-23
[QUOTE=msmith]Hi,

Assuming it recognized your keyboard correctly, you'll need to escape to a console with CTRL+ALT+F1. (You can get back to your X session later with ALT+F7). Login as yourself to get a shell prompt. If it's a usb mouse, type:

$ lsmod | egrep hid

If it's a usb mouse and you don't see output that looks something like this:

usbhid                 29376  0
usbcore               107384  3 usbhid,uhci_hcd

, you'll need to load the usbhid (human interface device) driver with modprobe.

If it isn't a usb mouse, you'll need the spcific driver for it.

Then you'll need to edit /etc/X11/xorg.conf or /etc/X11/XFree86.conf 

The relevant section in mine looks like this:

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

There may be other things that need to be done too, but this should get you started.[/QUOTE]
 It didin't work.

My computer is quite old, it has a serial mouse. The mainboard included mouse drivers just for DOS. I don't know how to edit /etc/X11/xorg.conf or /etc/X11/XFree86.conf either.

I'm sorry, I'm a total newbie.

---

