---
title: "Mouse moves extremely slowly on first boot up"
date: 2014-12-14
forum: Hardware
---

### Post by inertiaO on 2014-12-14
I have had a problem with my mouse and keyboard moving very slowly from cold boot since reinstalling to 1410. When I reboot the computer the keyboard/mouse returns to normal functionality. It appears something is wrong with all my USB devices though, as the Wifi doesn't connect either.

Before rebooting today, I tried to just restart X server but when I closed the X session I saw this message

USB 2-4 device descriptor read/8 error -110

USB 2-4 device descriptor read/64 error -110

The weird thing is this only happens from a cold boot and normal functionality returns as soon as I reboot.

I have tried downgrading my kernel to Ubuntu 1404 kernel, since I didn't have this problem before upgrading but it didn't resolve anything. So it could be just a coincidence that it is a problem with 1410.

---

### Post by inertiaO on 2014-12-15
I have turned off USB 3 in the bios and the problem, so far, seems to have resolved itself. This is not an optimal solution, obviously. Any one have any ideas?

---

