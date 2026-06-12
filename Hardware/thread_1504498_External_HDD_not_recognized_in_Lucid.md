---
title: "External HDD not recognized in Lucid"
date: 2010-06-08
forum: Hardware
---

### Post by nowave7 on 2010-06-08
I've been trying to copy some files from my old(WinXP) to my new machine(Lucid), using the external hdd rack, inside of which is a Seagate Barracuda 7200, 200GB. The disk is not recognized at all on Lucid, while it works without a problem on WinXp. The dmesg shows the following:

```
1158.464044] usb 2-2: new full speed USB device using uhci_hcd and address 10
[ 1158.588025] usb 2-2: device descriptor read/64, error -32
[ 1158.812026] usb 2-2: device descriptor read/64, error -32
[ 1159.084028] usb 2-2: new full speed USB device using uhci_hcd and address 11
[ 1159.204053] usb 2-2: device descriptor read/64, error -32
[ 1159.428389] usb 2-2: device descriptor read/64, error -32
[ 1159.644028] usb 2-2: new full speed USB device using uhci_hcd and address 12
[ 1170.052127] usb 2-2: device not accepting address 12, error -110
[ 1170.164025] usb 2-2: new full speed USB device using uhci_hcd and address 13
[ 1180.572022] usb 2-2: device not accepting address 13, error -110
[ 1180.572048] hub 2-0:1.0: unable to enumerate USB device on port 2

```

The device node is not created and no modules are being loaded.
I've tried all of the USB ports with some USB sticks and all seems to be in order as far as the motherboard is concerned. Any ideas on this? TIA!

---

### Post by nowave7 on 2010-06-08
Apparently, some people had this problem with the testing version of Lucid: [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1458707]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1458707")
But this is the latest version, and not the testing one. Anyone had this with 2.6.32-22-generic-pae?

---

### Post by Krovas on 2010-07-03
> **nowave7 said:**
> Apparently, some people had this problem with the testing version of Lucid: [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1458707]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1458707")
But this is the latest version, and not the testing one. Anyone had this with 2.6.32-22-generic-pae?


I'm having the same bad behavior with my external SATA on 2.6.32-23 generic.

---

### Post by Krovas on 2010-07-03
I think I've found the problem, though I have no idea what to do about it"

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

