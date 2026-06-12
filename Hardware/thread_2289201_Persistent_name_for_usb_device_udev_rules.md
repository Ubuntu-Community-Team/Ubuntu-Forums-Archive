---
title: "Persistent name for usb device udev rules"
date: 2015-08-02
forum: Hardware
---

### Post by rabaggett on 2015-08-02
I've got two USB-Serial adapters that I wish to assign persistent names so I can pass them to a VirtualBox windows session. (It gets me out of the 'counterfeit' prolific chip problem to let Linux handle the USB drivers, then pass the serial ports to the VM)

I created the following udev rules in a file:

SUBSYSTEM=="tty", ATTRS{idVendor}=="076b",
ATTRS{idProduct}=="2303", ATTRS{serial}=="0000:00:12.0",
SYMLINK+="TYT"
SUBSYSTEM=="tty", ATTRS{idVendor}=="0403",
ATTRS{idProduct}=="6001", ATTRS{serial}=="AH02TV2V",
SYMLINK+="BAO"

If I plug in only one of the usb devices, all works correctly.

The problem: when the second device is inserted, both symlinks point to the second inserted device.

If i then unplug the first device, and re-insert, both symlinks then point to that device. WTF? Did I do something goofy with the syntax?

---

### Post by rabaggett on 2015-08-03
I found the problem! It seem there i something about the counterfeit Prolific chip's serial number. When I removed **ATTRS{serial}=="0000:00:12.0",** everything started working properly.

---

