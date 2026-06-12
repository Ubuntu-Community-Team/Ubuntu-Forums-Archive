---
title: "logitech mini dinovo"
date: 2009-11-04
forum: Hardware
---

### Post by strange. on 2009-11-04
hey guys im trying to get a logitech mini dinovo working on karmic but i cant get the bluetooth stick to work

strange@vision:~$ dmesg | grep HID
[    2.844096] generic-usb 0003:046D:C313.0001: input,hidraw0: USB HID v1.10 Keyboard [LITEON Technology USB Multimedia Keyboard] on usb-0000:00:06.0-2/input0
[    2.853612] generic-usb 0003:046D:C313.0002: input,hidraw1: USB HID v1.10 Device [LITEON Technology USB Multimedia Keyboard] on usb-0000:00:06.0-2/input1
[    2.853677] usbhid: v2.6:USB HID core driver
[    3.790150] generic-usb 0003:046D:C71E.0003: input,hidraw2: USB HID v1.11 Keyboard [Logitech Logitech BT Mini-Receiver] on usb-0000:00:06.0-1.2/input0
[    4.016461] logitech 0003:046D:C71F.0004: input,hiddev96,hidraw3: USB HID v1.11 Mouse [Logitech Logitech BT Mini-Receiver] on usb-0000:00:06.0-1.3/input0
[  515.357302] generic-usb 0003:046D:C01E.0005: input,hidraw4: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:04.0-3/input0
[  722.978979] generic-usb 0003:046D:C71E.0006: input,hidraw2: USB HID v1.11 Keyboard [Logitech Logitech BT Mini-Receiver] on usb-0000:00:04.0-2.2/input0
[  723.217343] logitech 0003:046D:C71F.0007: input,hiddev96,hidraw3: USB HID v1.11 Mouse [Logitech Logitech BT Mini-Receiver] on usb-0000:00:04.0-2.3/input0


thats what my dmesg shows so its in there but bluetooth says no bluetooth receivers
anyone have any ideas/

---

### Post by strange. on 2009-11-04
i see some people posting that they've used jaunty bluetooth package but i dont have a downgrade option in package manager can someone point me in the right direction?

---

### Post by strange. on 2009-11-04
bump :(

---

### Post by tatsujin on 2009-11-22
bump... same problem, or similar.
The dongle & keyboard worked fine after the upgrade to karmic, but after a recent update (don't know exactly, but within a few weeks) it stopped working.

Even tried the fix in [this test thread](http://ubuntuforums.org/showthread.php?t=1236358) but to no avail. If I changed that rules file, either pairing stopped working, or no difference, depending on which PID I included in the match (mine isn't included in that rule).

Side quest, is it possible to get a list of packages installed/updated between certain dates?

---

### Post by tatsujin on 2009-11-28
Any help or advice with this is greatly appreciated!

Here's what appears in my **/var/log/messages** when I attach the dongle:

```

[  226.740018] usb 3-2: new full speed USB device using uhci_hcd and address 6
[  226.921524] usb 3-2: configuration #1 chosen from 1 choice
[  226.924494] hub 3-2:1.0: USB hub found
[  226.926669] hub 3-2:1.0: 3 ports detected
[  227.205443] usb 3-2.2: new full speed USB device using uhci_hcd and address 
7
[  227.359519] usb 3-2.2: configuration #1 chosen from 1 choice
[  227.372717] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00
/0000:00:1a.0/usb3/3-2/3-2.2/3-2.2:1.0/input/input8
[  227.372796] generic-usb 0003:046D:C71E.0004: input,hidraw1: USB HID v1.11 Ke
yboard [Logitech Logitech BT Mini-Receiver] on usb-0000:00:1a.0-2.2/input0
[  227.446429] usb 3-2.3: new full speed USB device using uhci_hcd and address 
8
[  227.602530] usb 3-2.3: configuration #1 chosen from 1 choice
[  227.622264] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00
/0000:00:1a.0/usb3/3-2/3-2.3/3-2.3:1.0/input/input9
[  227.622406] logitech 0003:046D:C71F.0005: input,hiddev96,hidraw2: USB HID v1
.11 Mouse [Logitech Logitech BT Mini-Receiver] on usb-0000:00:1a.0-2.3/input0
[  227.877448] usb 3-2.1: new full speed USB device using uhci_hcd and address 
9
[  228.012513] usb 3-2.1: configuration #1 chosen from 1 choice

```

And **lsusb** reports this (relevant part):
```

Bus 003 Device 009: ID 046d:c709 Logitech, Inc. BT Mini-Receiver (HCI mode)
Bus 003 Device 008: ID 046d:c71f Logitech, Inc. 
Bus 003 Device 007: ID 046d:c71e Logitech, Inc. 

```

And this is when the rule in **/lib/udev/rules.d/70-hid2hci.rules** looks like this:
```

# Logitech devices (hidraw)
KERNEL=="hiddev*", ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c70[345bce]|c71[34bcef]", \
  RUN+="hid2hci --method=logitech-hid --devpath=%p"

```
That is, from the originally distributed file, I changed from "hidraw*" to "hiddev*" and added the c71e and c71f PIDs. No other changes have been made from Karmic files.

I'm guessing that the device 046d:c709 is some kind of "ghost" device created by the dongle driver or something. Because, if I remove the c71e/f from the PIDs in the rule, the 046d:c709 doesn't even appear in the lsusb output. However, that doesn't help me much...

And with these settings, pairing doesn't work, nor does the keyboard or mouse on the dinovo mini, of course. :-(

Any ideas?

---

### Post by tatsujin on 2009-12-09
> **tatsujin said:**
> Any help or advice with this is greatly appreciated!
...
Any ideas? Hm... now I guess we'll never know what happened, or what the problem was.
I changed the rules file back to its original state, and now the keyboard & mouse works fine again...  wtf.

---

