---
title: "small cheap usb mouse not recognized"
date: 2008-05-20
forum: Hardware
---

### Post by komputes on 2008-05-20
Got a cheap no-name "made in china" type usb mouse that is not recognized by ubuntu. I just assumed that something basic like a mouse wouldn't have this issue. here is the dmesg output. Seems to work on XP just not ubuntu.

```
[  175.339528] usb 4-4: USB disconnect, address 3
[  258.038567] usb 6-2: new low speed USB device using uhci_hcd and address 2
[  258.053229] usb 6-2: configuration #1 chosen from 1 choice
[  258.058792] usb 6-2: can't set config #1, error -32
[  260.970195] usb 6-2: USB disconnect, address 2
[  261.536183] usb 6-2: new low speed USB device using uhci_hcd and address 3
[  261.558823] usb 6-2: configuration #1 chosen from 1 choice
[  261.564421] usb 6-2: can't set config #1, error -32
```Any ideas on how to troubleshoot? Any similar experiences?

---

### Post by magicfab on 2008-05-20
Hey all

Komputes is a colleague. I am a bit puzzled by this. We tried the mouse on several systems and got the same output. The mouse is fine, under Windows Vista it works normally so this is not a hardware problem.

I am getting usbmon output and filing a bug later on today, will report back here.

---

### Post by dejuren on 2008-05-20
I tested the mouse with USB/PS2 adapter and that way it is working in Ubuntu. The USB ID of the mouse is:```
ID 09da:0006 A4 Tech Co., Ltd Optical Mouse WOP-35 / Trust 450L Optical Mouse
``` There are bugs in launchpad with this USB ID listed, but no one with problem with this (or this type of) mouse, I assume it just works there.

---

