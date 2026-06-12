---
title: "after kernel update problem with usb sticks (udev-problem?!?)"
date: 2006-02-11
forum: Hardware &amp; Laptops
---

### Post by pinky on 2006-02-11
hi!
i have installed linux 2.6.15 (self made).
If i put the usb stick into the laptop i get this message (/var/log/messages):
```

scsi.agent[4842]:           sd_mod: loaded sucessfully (for disk)

```

but the stick doesn't get mounted like before.

I think this is a problem with udev because my cardreader doesn't get recognized too until i start the corresponding udev-script for the cardreader by my self.

What's going wrong. Does the udev from ubuntu breezy doesn't work together with new 2.6.15 kernel? Or does something implicitly have to be activated in the kernel and i have forget it maybe (but i don't think so, i have used the config of the default kernel as base)?

---

