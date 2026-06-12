---
title: "format new disk hw?"
date: 2010-10-01
forum: Hardware
---

### Post by ottosykora on 2010-10-01
I have just bought new 2.5inch 500gb sata drive.

I connected it to my pc with external drive - usb adaptor.

But how to proceed now? How to initialize the sata disk hanging on the usb port? The gparted does not recognize it as it was not formated yet and not initialized.

Hw to make it work?

---

### Post by psusi on 2010-10-01
You mean it doesn't show up in gparted at all, or it shows up as unformatted?  If the latter, then... umm... format it?

---

### Post by ottosykora on 2010-10-01
it does not show up at all.

it is powered, it is running, but it is not initialized, e.g. it has no partition table or any similar record on it at all, it is simply new out of he box.

with IDE drives, I was often actually inserting them into a computer, running fdisk, so giving them the first idea of partitions and files systems.
But my computer does not have sata connector, the drive should be used with usb adaptor as it is connecte now.

---

### Post by psusi on 2010-10-01
Sounds like the enclosure isn't working.  Run tail -f /var/log/kern.log then plug the drive in and see what new messages show up.

---

