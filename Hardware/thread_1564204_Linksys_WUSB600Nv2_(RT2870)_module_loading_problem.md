---
title: "Linksys WUSB600Nv2 (RT2870) module loading problem"
date: 2010-08-30
forum: Hardware
---

### Post by mr_squeaky on 2010-08-30
Hi,

I'm trying to get a Linksys WUSB600N v2 working with Ubuntu 10.4 Lucid (2.6.32-21-generic, x86_64).

I've downloaded the 2010_0709_RT2870_Linux_STA_v2.4.0.1 driver source from the Ralink web site and modified the common/rtusb_dev_id.c to include the following device ID:

    {USB_DEVICE(0x1737,0x0079)}, /* Linksys WUSB600Nv2 */

which is based on the following output of lsusb:

Bus 002 Device 005: ID 1737:0079 Linksys

The drivers appeared to compile and install successfully, using make && make install.

However, when I plug the device in, I receive this in /var/log/kern.log:

... usb 2-4: new high speed USB device using ehci_hcd and address 5
... usb 2-4: configuration #1 chosen from 1 choice

but if I run 'modprobe rt2870sta' kernel reports:

... rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
... rtusb init --->
... usbcore: registered new interface driver rt2870

Any assistance would be greatly appreciated.

Thanks,
Rob.

---

### Post by mr_squeaky on 2010-09-01
I found several posts mentioning the RT3572 drivers, so I downloaded 2010_0709_RT3572_Linux_STA_v2.4.0.1, configured as per readme (and added device as above) and it's now working.

---

