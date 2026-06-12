---
title: "How do I find out what driver my hardware is using?"
date: 2015-02-26
forum: Hardware
---

### Post by cpt.mayhem on 2015-02-26
I had a good search and couldn't find anywhere how to find exactly what driver a piece of hardware is using.

I have found: ```
lshw
``` which seems to list the components attached to my motherboard e.g. what's plugged into each PCI slot

I have also found: ```
xinput list
``` which seems to give a list of the names and ids attached devices e.g. my wireless mouse, but I cannot infer the driver being used for this.

Is there a general command that will tell me the driver being used by a specific piece of hardware? In this instance, I am interested in my touchpad.

Thanks!

---

### Post by ajgreeny on 2015-02-26
is there a good reason, other than curiosity, for needing to know the details?  The drivers for most of the basic hardware is in the linux kernel and there is no need to know more than that.

If the touchpad is from synaptics the driver is already installed automatically and is called **xserver-xorg-input-synaptics** but there are some other touchpads used by laptop makers, and I'm unsure of them or their drivers.

Do you have a problem?

---

### Post by tgalati4 on 2015-02-26
```
lsusb
lsusb -vvv
lspci
lspci -vvv
lsmod
modinfo psmouse
```

Substitute *psmouse* with something that looks like a wireless mouse driver from *lsmod*.

Linux uses modules to interact with hardware.

---

### Post by Yellow Pasque on 2015-02-26
@tgalati4, some of those commands require sudo/root for full info, and it may be an overwhelming amount of info:
I think this would be more useful:
```
lspci -k
lsusb
lsusb -t
```

As for the touchpad, the text log /var/log/Xorg.0.log will probably give you more useful info than lsusb.

---

