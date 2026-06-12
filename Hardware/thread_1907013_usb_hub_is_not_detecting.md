---
title: "usb hub is not detecting"
date: 2012-01-10
forum: Hardware
---

### Post by supravat on 2012-01-10
Hi, I bought an "iBall Lappie Piano 423 4 Port USB Hub". It works fine with windows os but in Ubuntu is not detecting it. I am using Ubuntu 11.04 on my desktop. Please help me.

---

### Post by madvinegar on 2012-01-13
Plug it in before you switch on the laptop, and then switch the laptop on. See if the hub will be recognized.

Also, try in terminal (as root) to write "modprobe usb-storage" and see if it mounts it.

If it does, add the line "**usb_storage**" in your /etc/modules.

---

