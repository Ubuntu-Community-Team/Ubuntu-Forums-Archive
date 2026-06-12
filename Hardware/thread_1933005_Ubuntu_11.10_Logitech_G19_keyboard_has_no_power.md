---
title: "Ubuntu 11.10 Logitech G19 keyboard has no power"
date: 2012-02-28
forum: Hardware
---

### Post by pquest on 2012-02-28
I recently installed the new Ubuntu, and I can't get my G19 working. Here is what I am seeing:

[LIST]
[*]The Keyboard gets power before the the Kernel Gets loaded
[*]As soon as the Kernel starts, the Keyboard and the mouse both lose power (somewhat normal)
[*]The mouse gets power back, but the keyboard never does. I can't type with the keyboard at all.
[/LIST]

Everything I can find online to do with the G19 seems to assume that the basic keyboard functionality just works, and deals with getting all the bells and whistles working (I don't care about that part, I just want to be able to use it at all).

Does anyone have any suggestions?

---

### Post by pquest on 2012-02-28
Also, it is not the keyboard. The keyboard works in the bios menus and windows just fine.

---

### Post by pquest on 2012-02-28
Perhaps I should also add that this is happening on an Asus republic of gamers laptop. Does it have something to do with the laptop's built in keyboard?

---

### Post by pquest on 2012-02-28
I found the following using:

```
dmesg | grep usb
```

[  181.994958] hub 3-0:1.0: couldn't allocate port 1 usb_device


Although I don't exactly know the cause:

Plugging the keyboard into my single usb 3.0 port (I have 3 2.0's and 1 3.0)

caused the keyboard to immediately start up and this was found using the same command.

[  554.545498] usb 2-1.3: new high speed USB device number 4 using ehci_hcd
[  554.913252] usb 2-1.3.1: new low speed USB device number 5 using ehci_hcd
[  555.015260] input: G19 Gaming Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3.1/2-1.3.1:1.0/input/input16
[  555.015504] generic-usb 0003:046D:C228.0003: input,hidraw2: USB HID v1.10 Keyboard [G19 Gaming Keyboard] on usb-0000:00:1d.0-1.3.1/input0
[  555.021593] input: G19 Gaming Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3.1/2-1.3.1:1.1/input/input17
[  555.021966] generic-usb 0003:046D:C228.0004: input,hiddev0,hidraw3: USB HID v1.10 Device [G19 Gaming Keyboard] on usb-0000:00:1d.0-1.3.1/input1
[  555.093401] usb 2-1.3.2: new high speed USB device number 6 using ehci_hcd
[  555.216646] input: Logitech G19 Gaming Keyboard as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3.2/2-1.3.2:1.1/input/input18
[  555.217175] generic-usb 0003:046D:C229.0005: input,hiddev0,hidraw4: USB HID v1.11 Keypad [Logitech G19 Gaming Keyboard] on usb-0000:00:1d.0-1.3.2/input1

While this will do for now, the usb 3.0 port is in a very inconvenient location for this fix, so I would prefer to solve the problem with the original usb port. Any ideas?

---

