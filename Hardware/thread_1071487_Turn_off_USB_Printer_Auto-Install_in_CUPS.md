---
title: "Turn off USB Printer Auto-Install in CUPS"
date: 2009-02-16
forum: Hardware
---

### Post by southernborn88 on 2009-02-16
I have over 250 Ubuntu 7 desktops set-up all over. I am having an issue with USB printers being auto-added into CUPS. Whenever the printer USB is disconnected, and reconnected it adds a whole new printer in. This causes the user to have difficulty printing.

I have attached an image as a helper. The first printer is the one we installed ourselves through the CUPS interface. The next 2 were auto-added into the system when the USB was reconnected.

Any help on how to stop this would be greatly appreciated.

---

### Post by dmizer on 2009-02-16
Try deleting the duplicate printer, and change the default printer's URI to this:
```
hp:/usb/hp_LaserJet_3016?serial=00MXBM192756
```
See if that corrects your problem.

---

### Post by southernborn88 on 2009-02-16
Well that will be beneficial if another printer is never plugged into the system at all. Unfortunately we have upper management plugging in their own personal printers. Technically we aren't supposed to support them, but we haven't found a way to disable the auto-add permanently.

---

### Post by dmizer on 2009-02-16
What I'm suggesting here is that the URI for that printer shouldn't change if you use hp:/usb/hp_LaserJet_3016?serial=00MXBM192756 instead of the current default of usb://HP/LaserJet%203015

In other words, you're getting a new printer every time you plug it in because you installed the first one without the correct URI.

Edit:
If the URI changes every time you plug the printer in, then it's probably a bug.

---

### Post by southernborn88 on 2009-02-25
I tried this, and it still just adds the printer in a second time. Even using the URI format that you sent me.

---

### Post by dmizer on 2009-02-25
You should open a bug report.

Here's how: [http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)

---

