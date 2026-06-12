---
title: "USB HDD not mounting; dmesg showing error"
date: 2007-04-24
forum: Hardware &amp; Laptops
---

### Post by zekopeko on 2007-04-24
I have a Nexstar3 2.5" USB enclosure with a 100GB IDE Seagate drive.

When i plug it in it doesn't mount (my other ICYBOX disks mount without a problem). 
This USB/HDD worked under edgy without a problem and works under WinXP. it's NTFS formated.

Here is the relevant output of dmesg:

[ 5861.653346] usb 3-4: new high speed USB device using ehci_hcd and
address 4
[ 5861.765301] usb 3-4: device descriptor read/64, error -71
[ 5861.977213] usb 3-4: device descriptor read/64, error -71
[ 5862.189132] usb 3-4: new high speed USB device using ehci_hcd and
address 5
[ 5862.301100] usb 3-4: device descriptor read/64, error -71
[ 5862.517012] usb 3-4: device descriptor read/64, error -71
[ 5862.728935] usb 3-4: new high speed USB device using ehci_hcd and
address 6
[ 5863.136772] usb 3-4: device not accepting address 6, error -71
[ 5863.248739] usb 3-4: new high speed USB device using ehci_hcd and
address 7
[ 5863.652593] usb 3-4: device not accepting address 7, error -71

anybody have an idea whats wrong?

---

### Post by dannyboy79 on 2007-04-24
gogle is an invaluable resource. I found this within 2 minutes. Found here: [http://www.linux-usb.org/FAQ.html#ts6](http://www.linux-usb.org/FAQ.html#ts6)

A: This can be one of several problems: 

High speed devices sometimes have problems with cables used to connect them. They're more sensitive to signal quality issues than older usb 1.1 full or low speed devices. If the device works OK at full speed on the same system, after you "rmmod ehci-hcd", this is likely the problem you're seeing. There are a lot of things you can do to change signal quality. 
Use a different cable. Some are even marketed specifically for use with high speed devices. Most USB 1.1 cables work just fine at high speed, but the one you're using might be an exception (maybe it's been damaged). 
Switch to a different USB connector on your computer. Back panel connectors are often right on the motherboard, with much care taken to preserve signal quality. A front panel connector probably doesn't use cabling designed with USB in mind; and its cable could be damaged by bending, baking or something else even when it's not routed through the power supply. 
Use an external high speed hub. Those hubs have signal conditioning circuitry that may cover up certain flaws. 
Make sure your device is using its own external power supply, or that its battery is fully charged. 
You might be able to get the same device to work at high speed on a different machine. 
You may have some problem with your PCI setup that's preventing your USB host controller from getting hardware interrupts. (Current Linux 2.6 kernels will actually tell you when they notice this problem; see the "dmesg" output.) When Linux submits a request, but never hears back from the controller, this is the diagnostic you'll see. To see if this is the problem, look at /proc/interrupts to see if the interrupt count for your host controller driver ever goes up. If it doesn't, this is the problem: either your BIOS isn't telling the truth to Linux (ACPI sometimes confuses these things, or setting the expected OS to windows in your BIOS), or Linux doesn't understand what it's saying. 
Sometimes a BIOS fix will be available for your motherboard, and in other cases a more recent kernel will have a Linux fix. You may be able to work around this by passing the noapic boot option to your kernel, or (when you're using an add-in PCI card) moving the USB adapter to some other PCI slot. If you're using a current kernel and BIOS, report this problem to the Linux-kernel mailing list, with details about your motherboard and BIOS. 

and also here: [http://www.linux-usb.org/notAcceptFeedback.html](http://www.linux-usb.org/notAcceptFeedback.html)

---

