---
title: "nike+ won't mount correctly"
date: 2010-12-26
forum: Hardware
---

### Post by kr651129 on 2010-12-26
So the software runs fine in wine and virtual box.  Even the software made for linux fine.  However dmesg sends a diffrent story.

```

Device [Nike SportBand+] on usb-0000:00:1d.0-1/input0
[ 5930.593786] usb 6-1: USB disconnect, address 6
[ 5936.301345] usb 7-1: new low speed USB device using uhci_hcd and address 2
[ 5936.424071] usb 7-1: device descriptor read/64, error -71
[ 5936.809311] generic-usb 0003:11AC:4269.0005: hiddev96,hidraw0: USB HID v1.11


```

and when I run virtualbox to see if that will work, I can add the nikeplus usb device to the filters so XP can see it, but still no luck.

lsusb:
```

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 003: ID 11ac:4269  
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:63ee Microdia 
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

any ideas?

---

### Post by kr651129 on 2010-12-26
bump

---

### Post by kr651129 on 2010-12-28
solved, created a howto [here]("http://ubuntuforums.org/showthread.php?t=1654437")

---

