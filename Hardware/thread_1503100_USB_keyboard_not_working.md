---
title: "USB keyboard not working"
date: 2010-06-06
forum: Hardware
---

### Post by topgun_tapan on 2010-06-06
I have a usb keyboard which was working perfectly till now (about a year since i have been regularly using ubuntu). It suddenly stopped working. It stopped working when I connected a USB HDD. Now the keyboard works randomly .. working for a while and then stops working for a longer time. Here is the dmesg output :

```

[  705.817076] usb 5-1: device not accepting address 8, error -71
[  705.928032] usb 5-1: new low speed USB device using uhci_hcd and address 9
[  706.336060] usb 5-1: device not accepting address 9, error -71
[  706.448055] usb 5-1: new low speed USB device using uhci_hcd and address 10
[  706.568044] usb 5-1: device descriptor read/64, error -71
[  706.792049] usb 5-1: device descriptor read/64, error -71
[  707.008060] usb 5-1: new low speed USB device using uhci_hcd and address 11
[  707.128041] usb 5-1: device descriptor read/64, error -71
[  707.352052] usb 5-1: device descriptor read/64, error -71
[  707.456068] hub 5-0:1.0: unable to enumerate USB device on port 1

```

Based on the suggestions [here]("http://ubuntuforums.org/showthread.php?t=797789") i tried the following two things:
```
echo -1 >/sys/module/usbcore/parameters/autosuspend
echo Y > /sys/module/usbcore/parameters/old_scheme_first

```

However, i am still facing the same problem. Can anyone help me out with this ?

---

### Post by unknown_killer on 2010-06-06
I guess time to buy a new keyboard.

---

