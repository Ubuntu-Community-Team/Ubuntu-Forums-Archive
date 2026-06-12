---
title: "USB Not recognised"
date: 2010-04-17
forum: Hardware
---

### Post by dezgo on 2010-04-17
I'm frustrated. I've recently switched to Ubuntu and am really happy to be up and running without windoze, but now I can't get the OS to pickup my USB key. It was recognised fine before, but after a reboot it now doesn't come up.

It is a U3 cruzer, 8Gb. I'm plugging it in via a USB 2 hub. 

This whole thing worked fine before, but not anymore. After doing too much surfing to find a fix for this I did notice that dmesg is helpful for getting things going. I can see these lines in that dmesg output:

[   15.732018] usb 4-2: new full speed USB device using uhci_hcd and address 8
[   16.160014] usb 4-2: device not accepting address 8, error -71
[   16.276049] usb 4-2: new full speed USB device using uhci_hcd and address 9
[   16.692028] usb 4-2: device not accepting address 9, error -71
[   16.692043] hub 4-0:1.0: unable to enumerate USB device on port 2

I tried the stuff at [http://ubuntuforums.org/archive/index.php/t-797789.html](http://ubuntuforums.org/archive/index.php/t-797789.html) with no luck. ie. 
ran both these commands as root
echo Y > /sys/module/usbcore/parameters/old_scheme_first
echo -1 >/sys/module/usbcore/parameters/autosuspend

then rebooted.

Any help would really be appreciated.

Thanks.

---

### Post by dezgo on 2010-04-19
Please I really need a hand with this. Surely it can't be that hard to get ubunto to recognise my usb drive?? No one knows what might be causing this.

Any basic troubleshooting tips would be appreciated.

Cheers

---

### Post by geoffatmk on 2010-05-20
I am as frustrated as you with this.  It has wiped ut the functionality of my laptop when travelling.  I now have to email files back and forth.

Can we bump this?

Have searched on forums but found nothing to help.  The only difference I can see between Karmic and Lucid is that the acpi system now works.  Could this have something to do with it?  Cutting power to the USB ports? 

The other message I get is that the device cannot accept an address (number) so is it some form of permissions problem?  Only seems to affect usb sticks and drives, not my mouse.

Bump

---

