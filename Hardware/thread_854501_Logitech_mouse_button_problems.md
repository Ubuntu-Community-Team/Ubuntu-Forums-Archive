---
title: "Logitech mouse button problems"
date: 2008-07-09
forum: Hardware
---

### Post by goldmanns on 2008-07-09
Trying to get Logitech MX500 mouse working with all buttons under Ubuntu 8.04. AFAIK there are two routes: one is to use "mouse" driver on /dev/input/mice, second is "evdev" on /dev/input/by-id/usb...eventmouse device. If I use "mouse" driver I always lose two buttons - one of side buttons is treated the same as scroll up, and topmost 'zen' button on the mouse is always the same as middle-click. Now, on evdev all buttons work as expected BUT as soon as I switch mouse/kbd/monitor to second computer (I have KVM switch) Ubuntu loses the mouse and does not redetect when switching back. 

This is driving me nuts... I used evdev in Ubuntu Gutsy and never had any problems with the KVM switch. 

Any ideas what to do?

---

