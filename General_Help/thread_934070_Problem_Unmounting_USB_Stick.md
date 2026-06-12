---
title: "Problem Unmounting USB Stick"
date: 2008-09-30
forum: General Help
---

### Post by Mark76 on 2008-09-30
It would appear that

> /media/sdf1 is not in the fstab,

and that I am

> not root

How do I amend this annoying behaviour?

---

### Post by eentonig on 2008-09-30
Message 1 is the reason why you get message 2. By default, only root can mount/unmount devices. allthough, normally, Ubuntu is set up to allow the regular user to plug/unplug usb devices.

To solve your issue.

> sudo umount /media/sdf1

---

### Post by Mark76 on 2008-09-30
I'm not using a normal Ubuntu. How can I set it up to allow the regular user (me) to mount/unmount external devices?

---

