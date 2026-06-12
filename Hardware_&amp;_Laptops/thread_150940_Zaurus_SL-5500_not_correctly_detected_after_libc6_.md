---
title: "Zaurus SL-5500 not correctly detected after libc6 upgrade"
date: 2006-03-27
forum: Hardware &amp; Laptops
---

### Post by mark541 on 2006-03-27
I recently upgraded several packages when prompted by the update manager. After the update, my Zaurus SL-5500 is not being detected.

This is what now prints in /var/log/messages when I plug in the Zaurus:

Mar 26 23:22:56 localhost kernel: [  645.828295] usb 3-1: new full speed USB device using uhci_hcd and address 6
Mar 26 23:22:56 localhost kernel: [  646.269531] usb 3-1: new full speed USB device using uhci_hcd and address 7
Mar 26 23:22:57 localhost kernel: [  646.680816] usb 3-1: new full speed USB device using uhci_hcd and address 8
Mar 26 23:22:57 localhost kernel: [  647.152013] usb 3-1: new full speed USB device using uhci_hcd and address 9

The last successful detection as listed in /var/log/messages was this:

Mar 23 20:31:48 localhost kernel: [597892.282777] usb0: register usbnet at usb-0000:00:10.2-1, Sharp Zaurus SL-5x00, 66:f4:3f:a4:1a:16
Mar 23 20:31:49 localhost usb.agent[26086]:      usbnet: already loaded

The only thing upgraded since March 23 at 8pm (the time and date of the last successful detection) are these packages:

libc6-i686_2.3.5-1ubuntu12.5.10.1_i386.deb
locales_2.3.5-1ubuntu12.5.10.1_all.deb
libc6_2.3.5-1ubuntu12.5.10.1_i386.deb

I suspect the libc6 packages are to blame, but I'm not sure what to do next. 

Any suggestions? Do you think this will be fixed in the next release?

Mark

---

