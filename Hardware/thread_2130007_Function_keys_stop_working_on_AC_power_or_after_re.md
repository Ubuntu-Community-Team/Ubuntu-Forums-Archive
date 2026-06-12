---
title: "Function keys stop working on AC power or after reboot"
date: 2013-03-28
forum: Hardware
---

### Post by kcc12 on 2013-03-28
Hi, 

I am using Lubuntu 12.10 64-bit on a new Toshiba Satellite L840D laptop. I am having a problem with keyboard shortcuts that use the function keys: F9 to decrease volume, Alt-F4 to close windows, etc. Most of the time, these shortcuts work fine. However, they stop working altogether whenever I either wake up from suspend or plug in the power cord. 

This problem doesn't happen if the power cord is in when I turn the computer on - only when I insert the cord after it has been running on battery, and it doesn't happen when I wake up from hibernate - only from suspend. The problem disappears when I reboot or when I hibernate and wake up. 

The keyboard shortcuts that do not work are only the shortcuts containing function keys that are defined in the file .config/openbox/lubuntu-rc.xml. The function keys still work for shortcuts that are not defined in that file: e.g. pressing F1 still works to open help screens and F2 shows a power manager notification. And, all keyboard shortcuts defined in .config/openbox/lubuntu-rc.xml that don't use the F keys do still work (e.g. ctrl-alt-right to switch between desktops). 

Thanks for any help.

---

