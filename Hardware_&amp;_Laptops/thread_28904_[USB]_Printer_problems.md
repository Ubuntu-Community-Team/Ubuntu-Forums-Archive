---
title: "[USB] Printer problems"
date: 2005-04-22
forum: Hardware &amp; Laptops
---

### Post by Dracontopes on 2005-04-22
I have an Epson Stylus C62.

Ubuntu recognizes it good and I can install the driver.

Then when I am trying to print something, it always pauses. I check the status of the printer, this is what is says:

```

Paused: Unable to open USB device "usb://EPSON/Stylus%20C62": No such device

```

Something must be f***** here. (oh I'm running Breezy)
I've tried reinstalling the driver and selecting the printer port myself etc etc to no luck... :(

---

### Post by buz on 2005-04-22
Printing in breezy is  broken as udev is broken.

---

### Post by Dracontopes on 2005-04-22
[QUOTE=buz]Printing in breezy is  broken as udev is broken.[/QUOTE]
 Okay, that clears it up :)
So I guess it's waiting for an update right?

---

### Post by buz on 2005-04-23
Suppose it is. I should have listened and not gone to breezy... Downgrading it left me with a temporarily unbootable system (until I had reupgraded it again) so that's not an option either.

---

### Post by Knute on 2005-04-27
Here's the line that I added to /etc/udev/permissions.rules

```
BUS="usb", KERNEL="lp[0-9]*",   NAME="usb/%k",  MODE="0660", GROUP="lp"
```

I was having issues with the /dev/usb/lp0 (where the HP printer is connected) being created with the group being root.  I added this line to make it create with the group lp so that we can print.

---

### Post by Dracontopes on 2005-04-27
Hey thanks! 

Printing is back to *work*! :D :D :D

---

