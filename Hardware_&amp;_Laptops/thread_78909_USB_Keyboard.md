---
title: "USB Keyboard"
date: 2005-10-19
forum: Hardware &amp; Laptops
---

### Post by elky10 on 2005-10-19
Hi, I've been using Breezy with a PS2 connection keyboard, and I just replaced that with a USB keyboard.  Ubuntu no longer recognizes it, so I can't login.  Any suggestions?

---

### Post by marner on 2005-10-20
Yes.

With both of your keybords attached, log into root or su.
add "modprobe usbhid" and "/etc/init.d/hotplug restart"to your /etc/init.d/bootmisc.sh

Then, at the next restart, your usb keyboard should be working properly.

Hope I could help.

---

