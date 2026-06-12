---
title: "Help with external SATA drive."
date: 2010-07-01
forum: Hardware
---

### Post by Krovas on 2010-07-01
I recently upgraded my hard drive, and converted the old drive into external storage with one of those SATA->USB enclosure things.

The new external drive won't mount, at least more than a split second. Most of the time, it sits there and chatters like it's doing something, spins up and spins down, and spits a bunch of messages such as:

```
[ 1155.487164] usb 2-2: USB disconnect, address 4
[ 1155.840107] usb 2-2: new full speed USB device using ohci_hcd and address 5
[ 1156.190095] usb 2-2: device descriptor read/64, error -62
[ 1157.000129] hub 2-0:1.0: unable to enumerate USB device on port 2
[ 1159.160105] usb 1-2: new high speed USB device using ehci_hcd and address 30
[ 1160.332096] hub 1-0:1.0: unable to enumerate USB device on port 2
[ 1162.340089] usb 1-2: new high speed USB device using ehci_hcd and address 31
[ 1170.270071] usb 1-2: device not accepting address 31, error -71
[ 1170.390106] usb 1-2: new high speed USB device using ehci_hcd and address 32
[ 1181.760076] usb 1-2: device descriptor read/all, error -71
[ 1181.880069] usb 1-2: new high speed USB device using ehci_hcd and address 33
[ 1188.670071] usb 1-2: device not accepting address 33, error -71
[ 1188.800088] usb 1-2: new high speed USB device using ehci_hcd and address 34

```

The enclosure is listed as taking 160gb drives. This sort of behavior seems to be a common problem, yet I haven't found a solution of even a workaround. Any assistance would be a appreciated.

---

### Post by clrg on 2010-07-01
Does your enclosure have an external power supply? If yes, plug it in. The power from a single USB port may not be enough.

---

### Post by Krovas on 2010-07-02
No, but it has the extra plug for power, not that it makes any difference. Actually, it appears to be a hardware problem. It exhibits precisely the same behavior on a Windows machine.

---

### Post by Krovas on 2010-07-03
Now I'm not sure it is hardware. Today it mounts repeatedly for about five seconds at a time. When it does, it pops up in Nautilus and I can read the filesystem normally, then it goes away, after which it may or may not mount again. Why should it work, but only for five seconds at a time?

---

### Post by Krovas on 2010-07-03
I think I've found the problem, but I don't know what to do about it:

> On Thu, 23 Oct 2008, Larry Finger wrote:

> In my system, a number of messages that state "unable to enumerate USB device"
> are logged. These are intermittent and likely due to some race condition
> at bootup.
> 
> Some of these happen when the EHCI driver is loaded after UHCI or OHCI, which
> causes the device to be switched away from the other controller that's trying
> to enumerate it, at least momentarily. This type of message is logged at most
> once for each hub and occurs in about 70% of my reboots.

This is normal; it is caused by userspace loading the drivers in the
wrong order.  ehci-hcd is supposed to be loaded before uhci-hcd or
ohci-hcd, not after.  There's no point trying to change the kernel to
avoid it.

> A more insidious form of the message occurs hundreds of times in about 10% of
> reboots. They continue until the system is rebooted. This patch limits the
> number of these messages to 20. Once the actual cause of this message is
> located, this patch can be reverted.

I would prefer to attack this problem directly rather than wallpaper 
over it.  Can you provide more information?  For example, a dmesg log 
with CONFIG_USB_DEBUG and CONFIG_PRINTK_TIME enabled would help.  It 
might also help to know what the devices which can't be enumerated 
actually are.

Alan Stern


[http://lkml.org/lkml/2008/10/24/209](http://lkml.org/lkml/2008/10/24/209)

---

