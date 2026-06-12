---
title: "Laptop keyboard/mouse partially responsive"
date: 2010-12-30
forum: Hardware
---

### Post by spartan223193 on 2010-12-30
My built in keyboard and mouse touch pad occasionally stop responding and are unable to be used with the exception of ctrl alt delete. When the menu asking me to shut down, suspend, log off, ext. comes up them mouse works there but nowhere else. Any help you can offer would be appreciated, thank you.

---

### Post by softwarejonas on 2010-12-30
Hi!
Can you provide the contents of the X log files located at /var/log/Xorg.0.log ?
 -- Jonas

---

### Post by spartan223193 on 2010-12-31
I have placed the Xlog contents in the attachment in the original post.

---

### Post by softwarejonas on 2011-01-01
Can you reproduce the error somehow? And please take a look at /var/log/messages once the error appears...
(tail /var/log/messages)

---

### Post by cavalier911 on 2011-01-01
See if booting the kernel with **acpi=off** stops the problem.
Power on then hold shift key if grub menu is hidden.
Highlight the boot entry in grub menu then hit e key for edit.
Add acpi=off after linux /boot/vmlinuz  quiet splash
Ctrl+x to boot

---

### Post by spartan223193 on 2011-01-07
The issue seems to have gone away after I disabled the default option to disable the track pad while typing. Thank you all for your time and feedback.

---

