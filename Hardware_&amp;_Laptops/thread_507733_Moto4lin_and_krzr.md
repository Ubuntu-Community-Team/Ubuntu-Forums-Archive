---
title: "Moto4lin and krzr"
date: 2007-07-23
forum: Hardware &amp; Laptops
---

### Post by kbm on 2007-07-23
I am working with kubuntu feisty fawn (upgraded from edgy if that matters).  I added the moto4lin package and have it configured to where it knows the phone is plugged in or unplugged, but never get a device created.  The usb devices list finds the phone (as does the 'update devices' in moto4lin) - so the system knows that the phone is there.  I don't know that the cpc_acm stuff is working (or installed) at all though.  Nor do I know if I have udev set up correctly to create the device.

When I plug the phone in, messages shows me the following:
Jul 22 19:31:31 ajax kernel: [  495.873919] usb 3-1: new full speed USB device using uhci_hcd and address 2
Jul 22 19:31:31 ajax kernel: [  496.036981] usb 3-1: configuration #1 chosen from 1 choice

dmsg is silent.  From other posts/pages, I expected something about the cpc_acm driver (usb devices shows no driver attached).

I added a rule to my udev symlinks rules:
# Create /dev/usb/acm/0 symlink for Motorola Phone
KERNEL=="ttyACM0", SYSFS{product}=="Motorola K1m*", SYMLINK+="usb/acm/0"

but I'm pretty sure it's both wrong and not getting that far because of the no driver thing.  Any ideas on which part(s) I have messed up?  Also, what is meant by 'configuration #1 chosen from 1 choice'?  Where do I find these choices?

Thanks for any help, this one has gotten under my skin!  So close, but no cigar.  Had it failed outright, I probably could have turned away, but to be just a device creation away - can't stop thinking about it!

---

