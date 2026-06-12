---
title: "Logitech Bluetooth Mouse and Keyboard"
date: 2007-05-03
forum: Hardware &amp; Laptops
---

### Post by erlanning on 2007-05-03
Ubuntu Fiesty Fawn
Logitech Bluetooth Mouse and Keyboard (MX1000 & MX5000) which connect via a USB dongle.

Keyboard works fine through GRUB

No keyboard and mouse functionality at login screen

The following lines have been input into /etc/default/bluetooth
BLUETOOTH_ENABLED=1
HIDD_ENABLED=1
HIDD_OPTIONS="-i --connect 00:07:61:36:24:D2 --connect 00:07:61:34:64:DD --server"

and "hidp" has been added to etc/modules.

It should be noted this worked an hour ago before I reinstalled the system.

I can manually enable both the keyboard and the mouse be either using (obviously I use another keyboard and mouse for this, a USB Logitech RF Wireless... maybe there is a conflict here?  I don't think so though)

sudo hidd --search
or
sudo hidd --connect baddr

But the above to commands work inconsistently.


Any help would be appreciated.

---

### Post by johndoesacc on 2007-05-08
I have a cordless desktop MX for bluetooth and it seems to work if i unplug it and plug it into a new usb port.

Every time i boot up i have to do that to make it work. It's an annoyance, but good enough for me to use it.

Any ideas to make it stick?

---

### Post by erlanning on 2007-05-14
The following is yet to be tested on Ubuntu...
However,
I installed Fedora Core 6 the other day.
Worked fine with the bluetooth.
Applied the recommened updates and bluetooth stopped working.
Removed the bluetooth updates, and it works fine.
It looks like whatever the latest version of the bluetooth drivers does not function well with this model.
Will get details and post.

---

