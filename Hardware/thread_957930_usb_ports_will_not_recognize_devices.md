---
title: "usb ports will not recognize devices"
date: 2008-10-24
forum: Hardware
---

### Post by the_fury on 2008-10-24
sorry, I couldn't think of a way to express this in the title. My USB ports work fine - when the devices are connected before I start the computer (for example, if I connect them and then restart, they will work. if I insert them while my ubuntu is up, it will not.)
i ran ```
dmesg | tail
``` and this is what i got:

[   95.478617] wlan1: no IPv6 routers present
[  210.244857] usb 3-2.2: new full speed USB device using uhci_hcd and address 9
[  210.347784] usb 3-2.2: not running at top speed; connect to a high speed hub
[  210.374980] usb 3-2.2: configuration #1 chosen from 1 choice
[  210.499741] usblp0: USB Bidirectional printer dev 9 if 0 alt 0 proto 2 vid 0x04E8 pid 0x3272
[  210.499756] usbcore: registered new interface driver usblp
[  212.005694] audit(1224893873.399:3): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=6829 profile="/usr/sbin/cupsd" namespace="default"
[  347.638847] audit(1224894009.185:4): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=7227 profile="/usr/sbin/cupsd" namespace="default"
[  376.098299] usb 3-2.2: USB disconnect, address 9
[  376.098458] usblp0: removed

which makes absolutely no sense. please help me! thanks in advance.

- the_fury

---

### Post by Yellow Pasque on 2008-10-24
See if this helps and report the bug as instructed if it does:
[https://wiki.ubuntu.com/DebuggingPrintingProblems#AppArmor%20Protection%20of%20the%20printing%20system](https://wiki.ubuntu.com/DebuggingPrintingProblems#AppArmor%20Protection%20of%20the%20printing%20system)

---

### Post by the_fury on 2008-10-27
My problem isn't that it won't recognize USB devices, it will. It's just that it will only recognize them if they are inserted prior to startup. Perhaps it only checks the USB devices at startup and not after?

---

### Post by Yellow Pasque on 2008-10-27
Is this true of all USB devices or only your printer? Did you try what I linked you to? (i.e. run *sudo aa-complain cupsd* and then plug your printer in)
> If you have any problems with printing, try deactivating the AppArmor protection with sudo aa-complain cupsd. If this helps, look for messages containing audit in the /var/log/messages file. These show which components are accessed by the printing system for which there is no explicit permission given in /etc/apparmor.d/usr.sbin.cupsd. You can re-activate AppArmor via sudo aa-enforce cupsd. Report a bug, about the package "cupsys", so that we can correct the default configuration of AppArmor. 

---

