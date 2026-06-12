---
title: "can't detect printer (hp deskjet 3650)"
date: 2007-01-13
forum: Hardware &amp; Laptops
---

### Post by kasimir on 2007-01-13
I have a HP Deskjet 3650 that was working fine in Dapper until yesterday. Then, when I tried to print, the print job would just get stuck in the queue and nothing would happen. Various things I've tried to solve the problem:

[LIST]
[*]installed hplip, using the instructions at their website
[*]restarted the cups and hplip daemons
[*]tried adding the printer with gnome-cups-manager, cups web interface, and hp-setup
[/LIST]

All 3 give me "hp no_device_found". I know the USB port is seeing the printer because after I plug it in, "dmesg" gives me:

[17703202.504000] ohci_hcd 0000:00:0b.0: wakeup
[17703202.888000] usb 1-8: new full speed USB device using ohci_hcd and address 28
[17703203.120000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 28 if 0 alt 0 proto 2 vid 0x03F0 pid 0x7204

The printer works fine in Windows, so it's not a hardware problem.

---

### Post by kasimir on 2007-01-14
Bump.

---

### Post by kasimir on 2007-01-15
I figured it out. Apparently, at some point I did a "umount -a", followed by a "mount -a", but this doesn't remount everything completely. Among the devices not remounted is /sys. This is needed for all USB devices. Dismounting it resulted in my USB printer not working, along with my flash drive, mp3 player, etc.

If you have similar symptoms, check if /sys is mounted with
```
cat /etc/mtab | grep /sys
```
and you should get a line like "/sys /sys sysfs rw 0 0". If you don't get that, unplug all your USB devices and mount /sys with
```
sudo mount -t sysfs /sys /sys
```

Make sure it got mounted with the first command, plug back in your USB devices and you should be good.

---

