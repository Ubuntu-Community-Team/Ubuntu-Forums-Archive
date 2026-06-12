---
title: "Unable to prevent usb_storage kernel module from loading"
date: 2008-08-07
forum: General Help
---

### Post by matthurne on 2008-08-07
I am running hardy, x86.

I want to prevent the usb_storage kernel module from loading, but I can't seem to figure out how to do so.  I have the following in /etc/modprobe.d/blacklist-local :

blacklist usb_storage

I have used the same blacklist file in the past to prevent other kernel modules from loading, with success.  But it hasn't made any difference for me with the usb_storage module.  I ensure that the module isn't loaded by checking the results of lsmod, tail -f /var/log/messages, then plug in a USB mass storage device (I have a few), and see message that the usb_storage driver is loaded.  Checking the output of lsmod shows the module is in fact loaded.

I don't really understand what triggers the loading of the usb_storage module when a USB mass storage device is detected.  I figure its either udev or the kernel itself, or the combination of the two, but shouldn't blacklisting the module in modprobe's configuration prevent it from loading?

Thanks for reading...

---

