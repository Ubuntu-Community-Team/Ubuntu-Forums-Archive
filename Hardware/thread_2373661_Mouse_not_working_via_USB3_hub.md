---
title: "Mouse not working via USB3 hub"
date: 2017-10-08
forum: Hardware
---

### Post by tom129 on 2017-10-08
Hi,

I've got a bit of an odd problem with my USB mouse!

I recently purchased a new monitor (Dell U2715H) that has a built in USB 3 hub. I have connected my keyboard and mouse to this hub and then I connect the USB cable from the monitor's hub to either my laptop or my PC depending on which device I am going to use.
Both the PC and the Laptop are running Xubuntu 16.04 with the latest updates installed.

Everything works perfectly with my laptop I can use both the keyboard and mouse with it.

However on my PC the mouse will not work. The cursor is stuck in the middle of the screen and it does not respond to button presses.

My mouse is a **Mad Catz R.A.T.7** which did initially have problems but these were solved by adding the following to my X11 config (on both my PC and laptop):

 ```
Section "InputClass"
        Identifier "Mouse Remap"
        MatchProduct "Mad Catz R.A.T.7 Mouse"
        MatchDevicePath "/dev/input/event*"
        Option "ButtonMapping" "1 2 3 4 5 0 0 8 9 7 6 12 0 0 0"
EndSection
```

If I plug the mouse directly into a USB port on the PC it works correctly.

The output of **xsetpointer -l | grep Pointer** seems to show that the mouse is correctly detected as a pointer:

```
root@tom-pc:~# xsetpointer -l | grep Pointer
2: "Virtual core pointer"    [XPointer]
4: "Virtual core XTEST pointer"    [XExtensionPointer]
10: "HID 0566:3013"    [XExtensionPointer]
8: "HOLTEK USB-HID Keyboard"    [XExtensionPointer]
13: "Logitech USB Receiver"    [XExtensionPointer]
14: "Mad Catz Mad Catz R.A.T.7 Mouse"    [XExtensionPointer]
15: "Logitech USB Receiver"    [XExtensionPointer]
```

My PC is dual boot and if I boot into Windows 10 everything works correctly, there are no problems with the mouse at all.

I have noticed that sometimes during bootup the keyboard/mouse are not detected on the BIOS screen because the monitor wakes up a too slowly but replugging the hub USB cable makes it detect the devices.

Does anyone have any ideas? I find it odd that the keyboard works via the Hub and that the mouse is detected but does not actually move...

---

### Post by tom129 on 2017-10-08
A quick update. I've discovered that plugging the hub into a USB2 port on the PC rather than a USB3 port fixes the issue! This seems odd as I am plugging in to a USB 3 port on the laptop and that works fine.

---

