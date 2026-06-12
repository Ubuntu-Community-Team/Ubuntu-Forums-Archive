---
title: "Automount usb flash drive on insert"
date: 2009-06-28
forum: Hardware
---

### Post by gnerdman on 2009-06-28
I have a usb flash drive that I want automounted on insert on a specific directory.  I know the uuid of the flash drive, and have configured it automount where I want it at boot time via the fstab.  However, I want to be able to remove it and have it remount automatically in the same place when I reinsert it.  usbmount won't do it, because it only works via media type vs. uuid/specific mount point.  I have a feeling there's a solution in udev, but haven't been able to figure it out.  Can someone help?  I'm using UNR installed on a different flash drive on an Acer Aspire One.  TIA.

6/29/09 Solution

I figured it out myself, and it did involve udev.  Here's what worked, hopefully it's useful for someone else.  

Set up /etc/fstab to mount the drive on boot via uuid:

UUID=<uuid_of_your_flash_drive> /<mount>/<point>	ext3 defaults,auto	0	0

Install pmount and create a file in /etc/udev/rules.d called 60-automount-flash.rules that contains:

ACTION=="add",KERNEL=="sdb*", RUN+="/usr/bin/pmount --sync --umask 000 UUID=<uuid_of_your_flash_drive>"
ACTION=="remove", KERNEL=="sdb*", RUN+="/usr/bin/pumount UUID=<uuid_of_your_flash_drive>"
ACTION=="add",KERNEL=="sdc*", RUN+="/usr/bin/pmount --sync --umask 000 UUID=<uuid_of_your_flash_drive>"
ACTION=="remove", KERNEL=="sdc*", RUN+="/usr/bin/pumount UUID=<uuid_of_your_flash_drive>"

Run:

udevadm control --reload-rules

---

