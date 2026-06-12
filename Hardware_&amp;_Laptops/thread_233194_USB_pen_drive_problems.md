---
title: "USB pen drive problems"
date: 2006-08-09
forum: Hardware &amp; Laptops
---

### Post by Fritz Mock on 2006-08-09
I am having a little problem with my USB pen drive, when connecting it via the usb-hub in my display.

The pendrive works pretty well with ubuntu when I connect it directly to one of my 4 usb-ports of my computer!

When the pendrive is connected via my displays usb-hub the kernel detects the drive, however the icon on the desctop won't show up, neither does the drive apear in "places/computer" and the options for hotplug-media have no effect.
Although 'dmesg' tells me, that the device was recognized.
The drive can be mounted manually, and small read and writes will be possible. However I couldn't wait for 25 MB to be written and pulled the plug after 15 minutes. (When the pen is plugged into one of the computers ports, it takes about 40 Seconds to copy such a file.)
During that time writing to to pen-drive 'dmesg' reports a series of the following lines:

usb 1-2.2: reset full speed USB device using uhci_hcd and address 4

I already googled that message in hope for some answers, but I only found some hints to older issues in 2.6.7. kernels.

Is there anyone experiencing similar problems?
Are there some usb-hubs known to have hardware bugs to cause this?
Is there a known kernel issue, that fits to my problem?

---

