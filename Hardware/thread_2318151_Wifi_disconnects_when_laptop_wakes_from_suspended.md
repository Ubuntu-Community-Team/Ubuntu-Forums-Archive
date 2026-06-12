---
title: "Wifi disconnects when laptop wakes from suspended"
date: 2016-03-23
forum: Hardware
---

### Post by danielecortes-89 on 2016-03-23
I have Ubuntu 14.04 and after recent updates, every time i suspend  it, Wireless stops working. I have to restart it to get it working.

---

### Post by weatherman2 on 2016-03-23
Your recent updates probably included a kernel update?  The kernel includes drivers for the wireless card.  Could be a new kernel update broke something.  You can try an older kernel to see if your laptop still works OK with the old one.  You can choose one from the Grub boot menu you might get when boot the laptop.  If you don't get a menu, try holding the Shift key down when the laptop is restarting.  Then you can choose "previous versions" - go back to and older kernel and try it.

---

