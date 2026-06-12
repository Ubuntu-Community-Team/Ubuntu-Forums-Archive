---
title: "USB mouse crashes and disables all USB ports."
date: 2006-08-01
forum: Hardware &amp; Laptops
---

### Post by Frem on 2006-08-01
I have this USB mouse that works for a while, then crashes. When it dies, it seems to kill all the USB ports, I can't use a memory stick or anything.

Here is the last part of the dmesg log for the latest crash. I had the USB mouse and a keyboard plugged in. (Though this was my first time with the keyboard, and the mouse has been doing this for quite a while.)

[17179639.796000] NET: Registered protocol family 10
[17179639.796000] lo: Disabled Privacy Extensions
[17179639.796000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179639.796000] IPv6 over IPv4 tunneling driver
[17179650.664000] ath0: no IPv6 routers present
[17179660.528000] NET: Registered protocol family 17
[17179670.264000] psmouse.c: GlidePoint at isa0060/serio4/input0 lost synchronization, throwing 1 bytes away.
[17179675.992000] ath0: no IPv6 routers present
[17179803.428000] usb 1-2: USB disconnect, address 3
[17179807.428000] ohci_hcd 0000:00:13.0: IRQ INTR_SF lossage
[17179811.428000] ohci_hcd 0000:00:13.0: IRQ INTR_SF lossage
[17179811.556000] usb 1-3: USB disconnect, address 4
[17179815.556000] ohci_hcd 0000:00:13.0: IRQ INTR_SF lossage
[17179904.280000] usb 1-2: new low speed USB device using ohci_hcd and address 5

In the log, you can see that the mouse died, and both it and the keyboard stopped responding, so I unplugged them both, then replugged in the mouse.
The keyboard sent two "IRQ INTR_SF lossage" messages because I'm using a PS2-to-USB adapter, and I just have the keyboard plugged into it.

So, yeah. Anyone have any ideas on what is causing this and how to stop it?

---

### Post by Frem on 2006-08-08
Alright, since noone has answered this for a week, heres a bit more info I've discovered.

Apparently, the errors only get thrown out to dmesg when I have multiple USB devices plugged in. The mouse dies same an usual even if it's the sole USB device in the system, though.

dmesg output when mouse is only USB device:
```
[17231589.808000] usb 1-2: new low speed USB device using ohci_hcd and address 2
[17231591.160000] usbcore: registered new driver hiddev
[17231591.164000] input: MosArt Optical Mouse as /class/input/input4
[17231591.164000] input: USB HID v1.10 Mouse [MosArt Optical Mouse] on usb-0000:00:13.0-2
[17231591.164000] usbcore: registered new driver usbhid
[17231591.164000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver

```

Oh, and it still registerers disconnects, even though the mouse won't work.

I'm going to take a wild stab in the dark and say it seems like whatever the problem is is causing the USB ports to stop sending power to connected devices.

---

### Post by anti-fsck on 2006-12-22
Seeing a similar problem here, although I'm noticing that every time I use super user the USB interfaces all die an ignoble death.

---

### Post by anti-fsck on 2006-12-22
> **anti-fsck said:**
> Seeing a similar problem here, although I'm noticing that every time I use super user the USB interfaces all die an ignoble death.

OK, just updated the kernel from default to linux-686 and at least fixed the problem with su. USB mouse and drive all seem to be working happily rather than crashing at the first sign of mounting, which is encouraging.
I'll give it a few days, though, before thinking it's cured.

---

### Post by glx on 2006-12-29
Hello
I got the same problem since a lot of time under Linux. Indeed, I dont use linux during six months now..(I'm using FreeBSD instead!)
But I test Suse (10.1 and 10.2) Fedora Core (5 et 6) Mandriva (2007) and even ArchLinux...Same problems. After a couple of time, my mouse stops working for ever (I cant get it rework thx to unplug/replug...).
Now I'm using a 2.6.18 (fc6 not vanilla...).
I found a very old post on lkml with that problem: [http://lkml.org/lkml/2005/11/9/252](http://lkml.org/lkml/2005/11/9/252) ...

---

### Post by bodzasfanta on 2007-01-04
Hello!

I had a similar problem but thanks God someone told me a good way to fix it.

"In grub, hit e to edit the boot line. Then move the selection over the kernel line and hit e again. Move the cursor to the end of the line and add the following:
Code:

noapic irqpoll pci=routeirq

Then hit enter to get our of line editing mode and b to boot the modified kernel line.

This will set you up until you power down or reboot. Edit /boot/grub/menu.list to make it permanent." (thanks for Frem)

I hope I could help you

---

