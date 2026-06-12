---
title: "USB mouse &amp; keyboard: slowly responding"
date: 2006-10-23
forum: Hardware &amp; Laptops
---

### Post by fiuman on 2006-10-23
I have the following problem: after some inactivity time, my USB keyboard and mouse start responding really slowly.
Surely it is not related to X server, because the problem shows in console mode too.
No processes load CPU anomalously.
I guess it is related to ACPI and IRQ address conflict... 

Infact, i tried to boot the kernel with the option pci=noacpi and the problem showed immediately at startup.
Here's my kernel log (with pci=noacpi option):

```
Oct 23 12:02:52 ubuntu kernel: [   26.825007] usb 1-2: new low speed USB device using uhci_hcd and address 3
Oct 23 12:02:52 ubuntu kernel: [   29.865559] usbcore: registered new driver hiddev
Oct 23 12:02:52 ubuntu kernel: [   30.613295] input: Logitech USB Mouse as /class/input/input0
Oct 23 12:02:52 ubuntu kernel: [   30.613423] input: USB HID v1.10 Mouse [Logitech USB Mouse] on usb-0000:00:11.2-1
Oct 23 12:02:52 ubuntu kernel: [   31.362147] input: DARFON USB MULTIMEDIA KEYBOARD as /class/input/input1
Oct 23 12:02:52 ubuntu kernel: [   31.362165] input: USB HID v1.10 Keyboard [DARFON USB MULTIMEDIA KEYBOARD] on usb-0000:00:11.2-2
Oct 23 12:02:52 ubuntu kernel: [   32.610158] input: DARFON USB MULTIMEDIA KEYBOARD as /class/input/input2
Oct 23 12:02:52 ubuntu kernel: [   32.610173] input: USB HID v1.10 Device [DARFON USB MULTIMEDIA KEYBOARD] on usb-0000:00:11.2-2
Oct 23 12:02:52 ubuntu kernel: [   32.610217] usbcore: registered new driver usbhid
Oct 23 12:02:52 ubuntu kernel: [   32.610221] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Oct 23 12:02:52 ubuntu kernel: [   32.821364] lp0: using parport0 (interrupt-driven).
Oct 23 12:02:52 ubuntu kernel: [   32.952193] Adding 497972k swap on /dev/hda5.  Priority:-1 extents:1 across:497972k
Oct 23 12:02:52 ubuntu kernel: [   33.022628] EXT3 FS on hda2, internal journal
Oct 23 12:02:52 ubuntu kernel: [   33.591367] cdrom: open failed.
Oct 23 12:02:52 ubuntu kernel: [   34.266001] kjournald starting.  Commit interval 5 seconds
Oct 23 12:02:52 ubuntu kernel: [   34.266169] EXT3 FS on hda3, internal journal
Oct 23 12:02:52 ubuntu kernel: [   34.266176] EXT3-fs: mounted filesystem with ordered data mode.
Oct 23 12:02:52 ubuntu kernel: [   34.396476] NTFS driver 2.1.25 [Flags: R/O MODULE].
Oct 23 12:02:52 ubuntu kernel: [   34.428120] NTFS volume version 3.1.
Oct 23 12:02:56 ubuntu kernel: [   40.815801] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Oct 23 12:02:56 ubuntu kernel: [   40.815920] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Oct 23 12:02:56 ubuntu kernel: [   40.816022] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Oct 23 12:02:56 ubuntu kernel: [   41.321285] uhci_hcd 0000:00:11.2: Unlink after no-IRQ?  Controller is probably using the wrong IRQ.
```

Take a look at last line above all.

Any advice?

---

### Post by fiuman on 2006-10-24
](*,)

---

### Post by fiuman on 2006-10-25
update: with option acpi=off, same behaviour.

---

### Post by doctorius on 2006-10-26
I found this 'problem thread' 
[http://http://www.mail-archive.com/linux-usb-users@lists.sourceforge.net/msg17024.html]("http://http://www.mail-archive.com/linux-usb-users@lists.sourceforge.net/msg17024.html")
Their result seems to be to turn off irqbalance...
Hope it will help you...

---

### Post by fiuman on 2006-10-27
First of all, thanks for reply :)
The thread you quoted refers to unload a module, ehci, but it doesnt load at startup (i configured kernel with uhci, i have low speed USB).
I have tried to pass the following option to kernel in the grub menu.lst:
noapic nolapic

and seems to work fine... so i'll leave as it is now.
Thanks anyway :)

---

