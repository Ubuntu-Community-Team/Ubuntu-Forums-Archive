---
title: "IPW 2200bg firmware"
date: 2007-07-07
forum: Hardware &amp; Laptops
---

### Post by Chejo on 2007-07-07
I tried to update firmware on this card but it requires program called hotplug. I cannot install this program it shows me errors.


/usr/bin/install -c -D sbin/hotplug /sbin/hotplug
/usr/bin/install -c -d /etc/hotplug/{usb,pci}
/usr/bin/install -c -D etc/hotplug.d/default/default.hotplug /etc/hotplug.d/default/default.hotplug
for F in etc/hotplug/{*.{agent,rc},hotplug.functions} ; do \
            /usr/bin/install -c $F /etc/hotplug ; \
            done
/usr/bin/install: cannot stat `etc/hotplug/{*.{agent,rc},hotplug.functions}': No such file or directory
make: *** [install] Error 1


What should I do to install hotplug?

---

### Post by Swab on 2007-07-07
I don't think hotplug is used anymore, I think it was replaced by udev.

Edit: Sorry for a completely unhelpful response.

---

### Post by Chejo on 2007-07-07
How to use udev to update firmware?

---

