---
title: "Computer Will Not Rsume From Suspend"
date: 2009-02-04
forum: Hardware
---

### Post by hunterman439 on 2009-02-04
I have recently built my own computer and installed ubuntu 8.10. I liked it right away, but one of the first things I noticed is that my computer fails to suspend. I followed another user's advice and checked the /etc/default/acpi-support file, and found nothing wrong. I changed a setting to use S1 suspend instead of S3, and changed the BIOS settings to match this. This did not work either. I wonder if this is hardware related? When I turn the computer on the monitor light stays yellow, the mouse lights up when clicked, and the keyboard does nothing. Thanks for your help.

---

### Post by sedawk on 2009-02-04
What are you trying to do to make your computer resume from suspend?

Some computers resume when they detect mouse or keyboard activity,
but only if they are connected via PS/2 connectors. They fail to wakeup from
an USB keyboard or USB mouse.

So the only way of resuming from suspend is to press the power button.
If that one is not wired properly there might be problems too.

The solution might also be in the BIOS (e.g. not powering of USB), in the
configuration (setting "wakeup" values before going to suspend mode), etc.

---

### Post by hunterman439 on 2009-02-05
The bios is set so the computer resumes from suspend using a usb device, a ps/2 keyboard, a ps/2 mouse, and rtc alarm is disabled. I tried the mouse, the keyboard, and the power button and all of these turn on the computer, but I get a blank screen.

---

