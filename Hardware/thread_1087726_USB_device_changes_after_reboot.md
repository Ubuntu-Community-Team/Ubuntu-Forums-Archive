---
title: "USB device changes after reboot?"
date: 2009-03-05
forum: Hardware
---

### Post by feh on 2009-03-05
Hi folks.

I'm using a keyspan usb->serial adapter to sync my Palm Pilot with my laptop running Kubuntu 8.10. I just installed 8.10 a few weeks ago.

From what I can tell, the /dev/ttyUSBx device associated with the keyspan adapter is not static. After a reboot, I have to change the device in the syncing software.

Is there a way to nail down the USB device, so I don't have to play detective after a reboot?

Thanks!

---

### Post by Chaim Leib on 2009-10-20
This looks exactly like the sort of thing udev is designed to do.  In short, udev is designed to allow users to tie a certain /dev file to a certain device, rather than port on a computer, or some other unpredictable characteristic.  It works by testing user-specified device attributes, and creating a symlink for the device in /dev if it finds a match. The name of the symlink to create is specified by the user; in the case of a pda, this is usually /dev/pilot.

Since I do not have the device strings for your specific adapter, I can't be more specific.  You can probably find this information by connecting your device to USB and then looking at dmesg to see what the system likes to call the device.  Then you can test for that device name or driver in your udev rule.

You can see some udev rule examples and information at [http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html)

---

